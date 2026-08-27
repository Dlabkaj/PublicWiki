# Custom Matching

Extension point for supplying request-matching logic beyond WireMock's standard matchers.

## When to use

If WireMock's standard set of request matching strategies isn't sufficient, you can register one or more request matcher classes containing your own logic.

## Two attachment styles

Custom matchers can be attached to stubs in two ways:

1. **Directly to a stub via the Java API**, when using the local admin interface (by calling `stubFor(...)` on `WireMockServer` or `WireMockRule`).
2. **Via the extension mechanism**, then referenced from individual stubs by name.

As with response transformers, per-stub-mapping parameters can be passed to matchers.

## Inline matcher (Java, local server only)

Anonymous `RequestMatcherExtension` implementation:

```java
wireMockServer.stubFor(requestMatching(new RequestMatcherExtension() {
    @Override
    public MatchResult match(Request request, Parameters parameters) {
        return MatchResult.of(request.getBody().length > 2048);
    }
}).willReturn(aResponse().withStatus(422)));
```

Java 8+ lambda form:

```java
wireMockServer.stubFor(requestMatching(request ->
    MatchResult.of(request.getBody().length > 2048)
).willReturn(aResponse().withStatus(422)));
```

⚠️ Inline matchers of this form **can only be used from Java, and only when `stubFor` is being called against a local WireMock server**. An exception will be thrown if attempting to use an inline custom matcher against a remote instance.

Custom matchers can also be used in verification:

```java
verify(2, requestMadeFor(new ValueMatcher<Request>() {
    @Override
    public MatchResult match(Request request) {
        return MatchResult.of(request.getBody().length > 2048);
    }
}));
```

## Named matcher extension

Create a class extending `RequestMatcherExtension` and register it as an extension:

```java
public class BodyLengthMatcher extends RequestMatcherExtension {
    @Override
    public String getName() {
        return "body-too-long";
    }

    @Override
    public MatchResult match(Request request, Parameters parameters) {
        int maxLength = parameters.getInt("maxLength");
        return MatchResult.of(request.getBody().length > maxLength);
    }
}
```

Reference by name from a stub, passing parameters:

```java
stubFor(requestMatching("body-too-long", Parameters.one("maxLength", 2048))
    .willReturn(aResponse().withStatus(422)));
```

JSON equivalent uses a top-level `customMatcher` object with `name` and `parameters`:

```json
{
  "request": {
    "customMatcher": {
      "name": "body-too-long",
      "parameters": { "maxLength": 2048 }
    }
  },
  "response": { "status": 422 }
}
```

## Combining custom and standard matchers

Inline (Java, local only):

```java
stubFor(get(urlPathMatching("/the/.*/one"))
    .andMatching(new MyRequestMatcher()) // Will also accept a Java 8+ lambda
    .willReturn(ok()));
```

Named extension form works from Java and JSON:

```java
stubFor(get(urlPathMatching("/the/.*/one"))
    .andMatching("path-contains-param", Parameters.one("path", "correct"))
    .willReturn(ok()));
```

```json
{
  "request": {
    "urlPathPattern": "/the/.*/one",
    "method": "GET",
    "customMatcher": {
      "name": "path-contains-param",
      "parameters": { "path": "correct" }
    }
  },
  "response": { "status": 200 }
}
```

## Sources

- [Custom Matching | WireMock](https://wiremock.org/docs/extensibility/custom-matching/)
