# Spring Boot @ServiceConnection

Since **Spring Boot 3.1.0**, the `@ServiceConnection` annotation removes most of the wiring boilerplate between a Testcontainers container and Spring's data-source (and other) configuration. Confirmed by Spring's own 3.1 release notes, which introduce the `spring-boot-testcontainers` module and its `@ServiceConnection` annotation. (sources: https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.1-Release-Notes, https://spring.io/blog/2023/06/23/improved-testcontainers-support-in-spring-boot-3-1/) Before 3.1.0, connecting a Spring test to a Testcontainers-managed database required a `@DynamicPropertySource` method to inject `spring.datasource.url/username/password`.

## Baseline: `@DynamicPropertySource` wiring

Without `@ServiceConnection`, a JUnit 5 + `@DataJpaTest` test wires the container manually:

```java
@DataJpaTest
@Testcontainers
class BookmarkRepositoryTest {
    @Container
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:17");

    @DynamicPropertySource
    static void configureProperties(DynamicPropertyRegistry registry) {
        registry.add("spring.datasource.url", postgres::getJdbcUrl);
        registry.add("spring.datasource.username", postgres::getUsername);
        registry.add("spring.datasource.password", postgres::getPassword);
    }
    // ...
}
```

## With `@ServiceConnection`

Add the `spring-boot-testcontainers` dependency (`test` scope) and annotate the container field:

```java
@DataJpaTest
@Testcontainers
class BookmarkRepositoryTest {
    @Container
    @ServiceConnection
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:17");
    // no @DynamicPropertySource needed
}
```

Spring Boot inspects the container type and creates a matching `ConnectionDetails` bean, which the relevant auto-configuration then consumes — for a `Neo4jContainer` it produces `Neo4jConnectionDetails`, and the Neo4j driver is pointed at the container. `@ServiceConnection` covers the most commonly used technologies (databases, brokers, caches).

Corrected in REVIEW: the fallback for a type Spring cannot infer is **not** necessarily `@DynamicPropertySource`. Because Spring Boot cannot tell which image a bare `GenericContainer` runs, the official reference has you supply the hint through the annotation itself — `@ServiceConnection(name = "redis")` on a `GenericContainer<>("redis:7")` still yields the right connection details. The same `name` attribute overrides detection for custom or mirrored images (e.g. `registry.mycompany.com/mirror/myredis`). `@DynamicPropertySource` remains available, but it is the last resort, not the first. (source: https://docs.spring.io/spring-boot/reference/testing/testcontainers.html)

## `TestcontainersConfiguration` pattern

Rather than declaring the container in every test class, Spring Initializr-generated projects (with PostgreSQL + Testcontainers selected) create a `TestcontainersConfiguration` under `src/test/java`:

```java
@TestConfiguration(proxyBeanMethods = false)
class TestcontainersConfiguration {
    @Bean
    @ServiceConnection
    PostgreSQLContainer<?> postgresContainer() {
        return new PostgreSQLContainer<>(DockerImageName.parse("postgres:17"));
    }
}
```

Tests then just `@Import(TestcontainersConfiguration.class)`:

```java
@DataJpaTest
@Import(TestcontainersConfiguration.class)
class BookmarkRepositoryTest { /* ... */ }

@SpringBootTest(webEnvironment = RANDOM_PORT)
@Import(TestcontainersConfiguration.class)
class BookmarkControllerTest { /* ... */ }
```

Existing (non-Initializr) projects need to create the class by hand.

## Slice tests vs full integration tests

- **`@DataJpaTest`** loads only the persistence slice — ideal for repository tests where the DB is the only external dependency.
- **`@SpringBootTest`** boots the entire application context — used with `TestRestTemplate` (and `webEnvironment = RANDOM_PORT`) to hit real HTTP endpoints against real containerised dependencies.

Both patterns benefit equally from `@ServiceConnection`, and both are demonstrated in the JetBrains bookmarks sample against PostgreSQL 17 and Testcontainers 1.20.4.

## Related pitfalls

- **Avoid H2/in-memory substitutes for a Postgres/Oracle production stack.** Behaviour diverges — e.g., `INSERT ... ON CONFLICT DO NOTHING` is valid Postgres but fails on H2 with `Syntax error in SQL statement`, and H2's `ROWNUM()` has no direct Postgres equivalent *(needs second source)*. Using the same DB engine in tests is a large part of Testcontainers' value proposition.
- **`@Container` on a static field ⇒ one container per test class.** Making the field non-static gives one container per test method, which is heavily discouraged for perf reasons.
- **You don't have to call `stop()`.** Even without an explicit `container.stop()`, Testcontainers destroys containers via the Moby Ryuk sidecar on JVM exit.

## Related pages

- [[JUnit5Integration]] — the `@Testcontainers`/`@Container` extension used in these samples
- [[SingletonContainersPattern]] — the alternative when the same containers serve many test classes
- [[ContainerReuse]] — uses the older `@DynamicPropertySource` wiring shown as the baseline here

## Sources

- <https://blog.jetbrains.com/idea/2024/12/testing-spring-boot-applications-using-testcontainers/> — Siva Katamreddy, JetBrains Blog, 2024-12. Uses Testcontainers 1.20.4, Spring Boot 3.x, PostgreSQL 17, JUnit 5.
- <https://docs.spring.io/spring-boot/reference/testing/testcontainers.html> — Spring Boot reference, "Testcontainers". Added in REVIEW; authoritative for `@ServiceConnection` semantics and the `GenericContainer` `name` attribute.
- <https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.1-Release-Notes> and <https://spring.io/blog/2023/06/23/improved-testcontainers-support-in-spring-boot-3-1/> — Spring Boot 3.1 release notes. Added in REVIEW to confirm the 3.1.0 introduction.
