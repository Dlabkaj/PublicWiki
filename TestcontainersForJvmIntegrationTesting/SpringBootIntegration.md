# Spring Boot Integration

Spring Boot ships a first-class Testcontainers integration via the `spring-boot-testcontainers` module (test-scoped dependency required for service connections).

## Three ways to wire containers into a Spring Boot test

1. **As Spring beans** — declare an `@Bean` method returning the container in a `@TestConfiguration(proxyBeanMethods = false)` class and `@Import` it into the test. Lifecycle then follows Spring bean lifecycle.
2. **Via the JUnit extension** — apply `@Testcontainers` on the class and `@Container` on a `static` field. Instance lifecycle is managed by Testcontainers.
3. **Via an interface + `@ImportTestcontainers`** — declare static `@Container` fields on an interface, then reference the interface from `@ImportTestcontainers(MyContainers.class)` inside a `@TestConfiguration`. Enables reuse across test classes.

## Lifecycle — the Spring bean vs. JUnit-extension trap

- **Spring-managed containers**: container beans are *created and started before all other beans* and *stopped after all other beans are destroyed*. Instance lives once per Spring `ApplicationContext` and is retained across multiple test classes that share the cached context.
- **Testcontainers-managed (JUnit extension) containers**: stopped after the test class (static field) or after each method (instance field).
- ⚠️ **Documented pitfall**: Spring's `TestContext` framework caches an `ApplicationContext` and reuses it for later classes. If that cached context holds beans depending on a Testcontainers-managed container that has *already* been stopped, later tests or destruction callbacks may fail. The official recommendation is to **prefer Spring bean management or `@ImportTestcontainers`** whenever the context is expected to be cached.

## Service Connections — `@ServiceConnection`

Annotating a container field (or `@Bean`-returned container) with `@ServiceConnection` causes Spring Boot to auto-configure the matching `ConnectionDetails` bean, **overriding any connection-related configuration properties**.

Detection rule:
- **Static field**: Spring calls `Container.getDockerImageName().getRepository()` to look up the factory.
- **`@Bean` method**: Spring uses the *return type* (not the image, to avoid eager init). Works for typed containers (`Neo4jContainer`, `RabbitMQContainer`, …) but not `GenericContainer` — for `GenericContainer` you must set `@ServiceConnection(name = "redis")` (or the appropriate name) as a hint.
- Same `name` attribute can also override the matched factory for custom image mirrors (e.g. `registry.mycompany.com/mirror/myredis`).

Built-in `ContainerConnectionDetailsFactory` matches (partial list):

| ConnectionDetails | Matched on |
|---|---|
| `JdbcConnectionDetails`, `R2dbcConnectionDetails`, `FlywayConnectionDetails`, `LiquibaseConnectionDetails` | `JdbcDatabaseContainer` subclasses (PostgreSQL, MySQL, MariaDB, MSSQL, Oracle XE/Free, ClickHouse) |
| `MongoConnectionDetails` | `MongoDBContainer`, `MongoDBAtlasLocalContainer` |
| `Neo4jConnectionDetails` | `Neo4jContainer` |
| `KafkaConnectionDetails` | `KafkaContainer`, `ConfluentKafkaContainer`, `RedpandaContainer` |
| `RabbitConnectionDetails` | `RabbitMQContainer` |
| `DataRedisConnectionDetails` | `RedisContainer`, `RedisStackContainer`, or image `redis` / `redis/redis-stack[-server]` |
| `CassandraConnectionDetails` | `CassandraContainer` |
| `CouchbaseConnectionDetails` | `CouchbaseContainer` |
| `ElasticsearchConnectionDetails` | `ElasticsearchContainer` |
| `PulsarConnectionDetails` | `PulsarContainer` |
| `ActiveMQConnectionDetails` | image `symptoma/activemq` or `ActiveMQContainer` |
| `ArtemisConnectionDetails` | `ArtemisContainer` |
| `LdapConnectionDetails` | image `osixia/openldap` or `LLdapContainer` |
| `Otlp{Logging,Metrics,Tracing}ConnectionDetails` | image `otel/opentelemetry-collector-contrib` or `LgtmStackContainer` |
| `ZipkinConnectionDetails` | image `openzipkin/zipkin` |

By default *all* applicable connection details are created (e.g. `PostgreSQLContainer` yields both JDBC and R2DBC). Use the `type` attribute of `@ServiceConnection` to restrict. `RabbitStreamConnectionDetails` is the one exception — it must be opted into via `type`, and the container must expose port `5552`.

### SSL with service connections

`@Ssl`, `@JksKeyStore`, `@JksTrustStore`, `@PemKeyStore`, `@PemTrustStore` configure **client-side** SSL on a service connection; you still have to enable SSL server-side inside the container yourself. Supported for Cassandra, Couchbase, Elasticsearch, Kafka, MongoDB, RabbitMQ, RabbitMQ Streams, Redis. `ElasticsearchContainer` additionally supports auto-detection of server-side SSL when annotated with `@Ssl` alone.

## `@DynamicPropertySource` — the escape hatch

A `static` method annotated with `@DynamicPropertySource` receives a `DynamicPropertyRegistry` and can push values into the `Spring Environment` after the container has started (e.g. `registry.add("spring.neo4j.uri", neo4j::getBoltUrl)`). More verbose than `@ServiceConnection` but works for anything Spring Boot doesn't ship a factory for.

(source: https://docs.spring.io/spring-boot/reference/testing/testcontainers.html)
