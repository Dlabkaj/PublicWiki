# Singleton Containers Pattern

The **singleton containers pattern** starts required containers once in a common abstract base class and reuses them across all integration test classes. It exists to avoid the growing cost of starting containers per test class as the suite grows.

## Base class shape

Containers are declared as `static` fields on an abstract base class and started from a `static {...}` initializer block. Test classes then `extends AbstractIntegrationTest` and reuse the same container instances.

Example structure (Postgres + Kafka):

```java
public abstract class AbstractIntegrationTest {
    static PostgreSQLContainer postgres = new PostgreSQLContainer("postgres:16-alpine");
    static ConfluentKafkaContainer kafka   = new ConfluentKafkaContainer("confluentinc/cp-kafka:7.8.0");

    static {
        postgres.start();
        kafka.start();
    }
}
```

Because the containers are started inside the class's static initializer, they start **once when the class is loaded** and are cleaned up by the **Ryuk** side-car container when the JVM exits — no explicit `stop()` is required.

## Parallel startup

Instead of starting containers sequentially in the static block, start them in parallel with `Startables.deepStart(postgres, kafka).join();` — this reduces total startup latency when multiple containers are needed.

## Common misconfiguration — do NOT combine with `@Testcontainers` / `@Container`

A frequent mistake is annotating the singleton base class with `@Testcontainers` and its fields with `@Container`:

```java
// DON'T DO THIS — containers will stop after each test class
@SpringBootTest(webEnvironment = RANDOM_PORT)
@Testcontainers
public abstract class AbstractIntegrationTest {
    @Container
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>(
        DockerImageName.parse("postgres:16-alpine"));
    // ...
}
```

The `@Testcontainers` extension **stops containers at the end of each test class**. In Spring Boot tests, the framework caches and reuses the ApplicationContext across subsequent test classes — but the container it points at has already been stopped, causing connection failures on the next class that runs.

**Correct pattern:** use a plain static initializer (or `@BeforeAll`) to start the containers and omit both `@Testcontainers` and `@Container`.

## When to use vs. per-class containers

- **`@BeforeAll` / `@AfterAll` lifecycle callbacks** — explicit control over startup/shutdown, single test class scope.
- **`@Testcontainers` / `@Container` extension annotations** — less boilerplate, single test class scope.
- **Singleton containers (this page)** — share one container instance across many test classes; recommended once the suite has more than a handful of integration test classes.

Starting a new container per test method (instance fields with `@Container` on non-static or `@BeforeEach`/`@AfterEach`) is explicitly **not recommended — resource-intensive**.

## Prerequisites for the referenced examples

Java 17+, a Docker environment supported by Testcontainers, and the following test dependencies (versions from the source guide, may be outdated): `org.testcontainers:testcontainers-junit-jupiter:2.0.4`, `org.testcontainers:testcontainers-postgresql:2.0.4`, `org.junit.jupiter:junit-jupiter:5.10.2`.

Note (REVIEW): [[JUnit5Integration]] quotes `2.0.5` for the same `testcontainers-junit-jupiter` artifact. Not a contradiction — the two guides simply pin different patch releases of the 2.x line in their examples, and both exist on Maven Central. Pin whatever the current 2.x release is rather than either literal.

## Related pages

- [[JUnit5Integration]] — the `@Testcontainers`/`@Container` extension this pattern deliberately avoids
- [[ManualLifecycleControl]] — bare `start()`/`stop()` and try-with-resources
- [[ContainerReuse]] — reuse across JVMs/runs, a different mechanism from this in-JVM sharing

## Sources

- Docker Docs — *Testcontainers container lifecycle management using JUnit 5 — Singleton containers pattern*: https://docs.docker.com/guides/testcontainers-java-lifecycle/singleton-containers/
