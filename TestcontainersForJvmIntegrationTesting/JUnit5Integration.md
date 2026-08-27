# JUnit 5 (Jupiter) Integration

Testcontainers exposes a JUnit Jupiter extension in a **separate artifact**: `org.testcontainers:testcontainers-junit-jupiter` (test scope).

## Wiring

- Add `@Testcontainers` to the test class — this registers the extension.
- Annotate container fields with `@Container` — the extension calls the `Startable` interface's lifecycle methods on each one.

## Field scope decides lifecycle

| Field kind | Behavior |
|---|---|
| **`static` field with `@Container`** | Shared across all methods of the class. Started **once** before any test method runs; stopped after the last test method finishes. |
| **Instance field with `@Container`** | Started and stopped **for every test method**. |

You can mix both in one class, e.g. a shared `static MySQLContainer` alongside a per-method `PostgreSQLContainer` instance field.

## Nested test classes

- Shared (`static`) containers can **only** be declared on the top-level test class — JUnit 5 nested classes must be non-`static`, so they cannot host static fields.
- An instance container declared on the outer class is **restarted** for methods inside a `@Nested` class.
- A container declared inside a nested class is only visible inside that nested class.

## Documented limitations

- ⚠️ **Parallel test execution is unsupported.** The extension has only been tested with sequential execution and using it with parallel execution "may have unintended side effects."

## Singleton container pattern

The docs explicitly note that the singleton container pattern (manual lifecycle, one instance for the whole JVM) remains a valid option under JUnit 5 as an alternative to the extension. Full treatment: [[SingletonContainersPattern]]. See also [[ManualLifecycleControl]].

## Dependency

```groovy
testImplementation "org.testcontainers:testcontainers-junit-jupiter:2.0.5"
```

```xml
<dependency>
  <groupId>org.testcontainers</groupId>
  <artifactId>testcontainers-junit-jupiter</artifactId>
  <version>2.0.5</version>
  <scope>test</scope>
</dependency>
```

Resolved in REVIEW: `2.0.5` is genuine — Testcontainers 2.x **renamed** the artifact. On the 1.x line the coordinates are `org.testcontainers:junit-jupiter` (e.g. `1.20.4`, `1.21.4`); on 2.x they are `org.testcontainers:testcontainers-junit-jupiter`. Both artifacts exist on Maven Central, so the low-looking number is a new major version, not an error. (sources: https://central.sonatype.com/artifact/org.testcontainers/testcontainers-junit-jupiter, https://central.sonatype.com/artifact/org.testcontainers/junit-jupiter)

(source: https://java.testcontainers.org/test_framework_integration/junit_5/)
