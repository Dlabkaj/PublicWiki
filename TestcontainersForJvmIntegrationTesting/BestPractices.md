# Testcontainers Best Practices (JVM)

Do's and don'ts distilled from the Docker Testcontainers "Best Practices" blog post (Java examples, but concepts apply to other Testcontainers bindings).

## Don't rely on fixed host ports

Binding a container to a fixed host port (e.g. Postgres on 5432 of the host) breaks in three predictable ways:

- Local port collision if another process (or another dev on the team) already owns that port.
- CI pipelines running in parallel try to start multiple containers of the same type on the same fixed host port and collide.
- Local parallel test execution runs multiple instances of the same container simultaneously.

**Do** use dynamic port mapping. Expose the container port and read the mapped host port back from Testcontainers:

```java
GenericContainer<?> redis = new GenericContainer<>("redis:5.0.3-alpine")
    .withExposedPorts(6379);
int mappedPort = redis.getMappedPort(6379);
// or redis.getFirstMappedPort() when there is only one

PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine");
int mappedPort = postgres.getMappedPort(5432);
String jdbcUrl = postgres.getJdbcUrl();
```

Fixed host ports are acceptable for **local development** (constant port for DB tools) — Testcontainers Desktop offers this via its "fixed port" feature — but not for tests.

## Don't hardcode the hostname

Using `localhost` in test configuration works only when the Docker daemon is local and containers are reachable on `localhost`. It fails on **Remote Docker daemons** and Testcontainers Cloud.

**Do** call `container.getHost()` instead. In a Spring Boot test:

```java
@DynamicPropertySource
static void overrideProperties(DynamicPropertyRegistry registry) {
    registry.add("spring.redis.host", () -> redis.getHost());
    registry.add("spring.redis.port", () -> redis.getMappedPort(6379));
}
```

## Don't hardcode the container name

Setting a fixed container name via `withCreateContainerCmdModifier(cmd -> cmd.withName("postgres"))` breaks any scenario running two containers with that name simultaneously — most commonly parallel CI pipelines.

General rule from the post: *if a generic Docker feature is missing from the Testcontainers API, it is usually an intentional opinionated choice that pushes users toward integration-testing best practices.* `withCreateContainerCmdModifier` is available as an advanced escape hatch and should not be used to work around those design decisions.

## Copy files into containers rather than bind-mount them

Bind-mounting local files (`withFileSystemBind(...)`) works locally but breaks on Remote Docker daemons and Testcontainers Cloud because the file is not present on the remote host.

**Do** copy the file into the container instead:

```java
PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine")
    .withCopyFileToContainer(
        MountableFile.forClasspathResource("schema.sql"),
        "/docker-entrypoint-initdb.d/01-schema.sql");
```

`withCopyFileToContainer` keeps tests portable across local, remote-daemon, and Cloud environments.

## Pin image versions — never `latest`

`postgres:latest` (or any `:latest` tag) makes tests flaky when a new image version is published. Pin to the **same version used in production**:

```java
// Bad
new PostgreSQLContainer<>("postgres:latest");
// Good
new PostgreSQLContainer<>("postgres:15.2");
```

## Use the right container lifecycle strategy

Declaring the container as a `static` field on the test class starts one container for the whole class. Non-static fields start a fresh container **per test**, which is resource-intensive and can also fail if the Spring context is not recreated.

Anti-pattern noted in the post: applying `@Testcontainers` + `@Container` *and* also calling `container.start()` / `container.stop()` manually — one or the other, not both.

To speed up test suites with many test classes, use the **Singleton Containers Pattern** — full treatment in [[SingletonContainersPattern]], including the `@Testcontainers` pitfall that the anti-pattern above is one symptom of.

## Leverage framework integration

Spring Boot, Quarkus, and Micronaut all ship out-of-the-box Testcontainers integration; prefer that over rolling your own wiring:

- Spring Boot support for Testcontainers — see [[SpringBootServiceConnection]] for the `@ServiceConnection` mechanics.
- Quarkus DevServices using Testcontainers.
- Micronaut TestResources using Testcontainers.

## Prefer technology-specific modules over `GenericContainer`

Testcontainers ships modules for most common infrastructure (SQL databases, NoSQL stores, message brokers, search engines). They provide sensible defaults and typed accessors like `getJdbcUrl()` / `getBootstrapServers()`. Contrast:

Verbose `GenericContainer` version of Postgres — manual env vars, manual `LogMessageWaitStrategy`, hand-built JDBC URL:

```java
GenericContainer<?> postgres = new GenericContainer<>("postgres:16-alpine")
    .withExposedPorts(5432)
    .withEnv("POSTGRES_USER", "test")
    .withEnv("POSTGRES_PASSWORD", "test")
    .withEnv("POSTGRES_DB", "test")
    .waitingFor(new LogMessageWaitStrategy()
        .withRegEx(".*database system is ready to accept connections.*\\s")
        .withTimes(2).withStartupTimeout(Duration.of(60L, ChronoUnit.SECONDS)));
postgres.start();
String jdbcUrl = String.format("jdbc:postgresql://%s:%d/test",
    postgres.getHost(), postgres.getFirstMappedPort());
```

Module version — one line for the container, one for the URL:

```java
PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:16-alpine");
String jdbcUrl = postgres.getJdbcUrl();
```

Check the Modules Catalog first; fall back to `GenericContainer` (or a custom subclass of it) only if no module exists.

## Use `WaitStrategy` — don't `Thread.sleep`

With `GenericContainer` or a custom module, wait for a real readiness signal instead of sleeping:

```java
// Bad
container.start();
Thread.sleep(2 * 1000);

// Good
GenericContainer<?> container = new GenericContainer<>("image:tag")
    .withExposedPorts(9090)
    .waitingFor(Wait.forLogMessage(".*Ready to accept connections.*\\n", 1));
container.start();
```

If no explicit `WaitStrategy` is configured, Testcontainers uses a **default strategy that checks connectivity of all exposed ports** from the host.

## Related pages

- [[SingletonContainersPattern]] — the lifecycle strategy this page recommends for large suites
- [[JUnit5Integration]] — `@Testcontainers`/`@Container` and the static-vs-instance field rule
- [[ContainerReuse]] — a further speed-up, local development only
- [[SpringBootServiceConnection]] — the Spring Boot framework integration referenced above
- [[ManualLifecycleControl]] — `start()`/`stop()` when no extension fits

## Sources

- Docker Blog — *Testcontainers Best Practices* (Siva Katamreddy, 2023-11-03): https://www.docker.com/blog/testcontainers-best-practices/
