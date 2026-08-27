# Manual Container Lifecycle Control

Testcontainers can be used without any test framework, controlling container start/stop directly from code. This is the fallback when JUnit/Spock extensions do not fit the setup.

## Starting and stopping in code

Containers expose `start()` and `stop()` methods. All container classes also implement `AutoCloseable`, so a try-with-resources block gives a strong guarantee that the container will be stopped even if the test throws.

```java
try (GenericContainer container = new GenericContainer("imagename")) {
    container.start();
    // ... use the container
    // no need to call stop() afterwards
}
```

The idiom removes the need for an explicit `stop()` call and pairs naturally with test methods that own their container for a single scope.

## Singleton containers pattern

Manual lifecycle control is also what the singleton pattern is built on: Testcontainers provides **no special support** for reusing one container across many test classes, so the recipe is a hand-written abstract base class with a `static` block, torn down by the Ryuk sidecar rather than by explicit `stop()` calls. Full treatment, including the Spring Boot pitfall and parallel startup: [[SingletonContainersPattern]].

## Related pages

- [[SingletonContainersPattern]] — sharing one container across many test classes
- [[JUnit5Integration]] — the `@Testcontainers` extension this page is the alternative to
- [[ContainerReuse]] — reuse requires manual lifecycle control, not the extension

## Source

- <https://java.testcontainers.org/test_framework_integration/manual_lifecycle_control/> — official Testcontainers for Java docs, "Manual container lifecycle control".
