# Reusable Containers

Container startup is the dominant cost of Testcontainers-driven integration tests. A container can be kept alive across test runs so subsequent runs skip the cold start. The blog source dates the feature to the **1.12.3** release and calls it *alpha* *(needs second source)*; the current official page titles it **"Reusable Containers (Experimental)"**, so treat the stage label as having moved from alpha to experimental rather than to stable. (source: https://java.testcontainers.org/features/reuse/)

## Three requirements to reuse

All three must be satisfied — miss one and Testcontainers falls back to starting a fresh container. Requirements 1 and 2 are confirmed by the official reference, which also documents `TESTCONTAINERS_REUSE_ENABLE=true` as an environment-variable equivalent to the properties-file flag. (source: https://java.testcontainers.org/features/reuse/)

1. **`.withReuse(true)` on the container definition** — a builder on `GenericContainer` (inherited by every module container).
2. **Opt-in in `~/.testcontainers.properties`** — the reuse flag is per-developer/per-CI-user, not per-project:
   ```
   testcontainers.reuse.enable=true
   ```
3. **Manual lifecycle control** — a singleton container or a `@BeforeAll`-started container. **The JUnit 4 `@Rule` and the JUnit 5 `@Testcontainers` extension both tear the container down after the test**, so neither is compatible with reuse.

## Reference singleton + Spring Boot wiring

The typical shape is an abstract base class combining `@SpringBootTest`, a static container with `.withReuse(true)`, and `@DynamicPropertySource` to inject the JDBC coordinates:

```java
@SpringBootTest(webEnvironment = RANDOM_PORT)
public abstract class BaseIT {
    static final PostgreSQLContainer<?> postgreSQLContainer;
    static {
        postgreSQLContainer = new PostgreSQLContainer<>(DockerImageName.parse("postgres:13"))
            .withDatabaseName("test").withUsername("duke").withPassword("s3cret")
            .withReuse(true);
        postgreSQLContainer.start();
    }

    @DynamicPropertySource
    static void datasourceConfig(DynamicPropertyRegistry registry) {
        registry.add("spring.datasource.url", postgreSQLContainer::getJdbcUrl);
        registry.add("spring.datasource.password", postgreSQLContainer::getPassword);
        registry.add("spring.datasource.username", postgreSQLContainer::getUsername);
    }
}
```

`@DynamicPropertySource` requires **Spring Boot 2.2.6+** (Spring Framework 5.2.5+). Confirmed independently by Spring's own announcement. (source: https://spring.io/blog/2020/03/27/dynamicpropertysource-in-spring-framework-5-2-5-and-spring-boot-2-2-6/)

## Reuse is keyed on configuration

Testcontainers reuses only when the container definition matches an existing one. **Image tag, database name, username, password, and other `.with*` calls all participate in the reuse key.** The official reference describes the same mechanism: a hash is computed from the container's configuration at startup, and a later request reuses the running container only when it hashes identically. (source: https://java.testcontainers.org/features/reuse/) Three tests declaring `postgres:10-alpine`, `postgres:13` with `differentDatabaseName`, and `postgres:13` with `test` respectively will each spawn their own container — none is reused. In practice this means every project that wants reuse benefits should standardise on a single container spec.

## Measured impact

On the author's machine, three integration tests took **~20 s cold** and **~10 s** when reusing containers — roughly a 2× speed-up for that workload *(needs second source)*. This is one person's single-machine measurement from a blog post, not a published benchmark; treat the 2× as an anecdote about the shape of the win, not a figure to plan against.

## Trade-offs and pitfalls

- **Containers keep running after tests finish.** If you work on multiple projects the leftovers accumulate; the author recommends `docker rm $(docker ps -a -q)` periodically to reclaim resources or avoid port/name conflicts.
- **State bleeds between runs.** Reuse only makes sense when either the container has no persistent state that matters, or the test cleans up (e.g., `todoRepository.deleteAll()` in `@AfterEach`, or a schema-recreate on each run).
- **Spring context caching multiplies connection pressure.** Spring Test may spawn several `ApplicationContext`s per suite, and all of them will connect to the single reused container — size the container to handle it.
- **Experimental feature.** The article called it alpha; the official page still marks it experimental, so behavior may change between Testcontainers versions.
- **Not for CI.** The official reference states outright that reusable containers are **not suited for CI usage** — the whole point is a container surviving between runs, which a clean CI agent neither has nor wants. Reuse is a local-development optimization. (source: https://java.testcontainers.org/features/reuse/)
- **Networks are not reusable.** Reuse in Testcontainers for Java does not support networks; attaching one changes the configuration and defeats reuse. (source: https://java.testcontainers.org/features/reuse/)

## Related pages

- [[SingletonContainersPattern]] — the manual-lifecycle base class reuse requires (requirement 3)
- [[JUnit5Integration]] — why `@Testcontainers`/`@Container` is incompatible with reuse
- [[SpringBootServiceConnection]] — the modern alternative to the `@DynamicPropertySource` wiring above

## Sources

- <https://rieckpil.de/reuse-containers-with-testcontainers-for-fast-integration-tests/> — rieckpil, "Reuse Containers With Testcontainers for Fast Integration Tests", published 2020-06-21, last updated 2025-09-08. Sample uses Spring Boot 2.6.0 + Testcontainers 1.16.2.
- <https://java.testcontainers.org/features/reuse/> — Testcontainers for Java, "Reusable Containers (Experimental)". Added in REVIEW to corroborate the reuse mechanism and the CI/networks caveats.
- <https://spring.io/blog/2020/03/27/dynamicpropertysource-in-spring-framework-5-2-5-and-spring-boot-2-2-6/> — Spring, announcing `@DynamicPropertySource`. Added in REVIEW.
