# Stub Priority

Numeric attribute controlling which stub wins when a request matches more than one mapping.

## Default resolution

- When multiple stub mappings would match the same request, WireMock uses the most recently added matching stub by default.
- When a stub does not specify a priority, it defaults to a priority of `5`.

## Priority range

- `1` is the highest priority.
- Java `Integer.MAX_VALUE` (i.e. `2147483647`) is the minimum priority.

## Setting priority

Java DSL uses `.atPriority(int)` on the stub builder; JSON uses the top-level `"priority"` field.

```java
// Catch-all case
stubFor(get(urlMatching("/api/.*")).atPriority(5)
    .willReturn(aResponse().withStatus(401)));

// Specific case
stubFor(get(urlEqualTo("/api/specific-resource")).atPriority(1) // 1 is highest
    .willReturn(aResponse()
        .withStatus(200)
        .withBody("Resource state")));
```

JSON equivalent:

```json
{
  "priority": 1,
  "request": {
    "method": "GET",
    "url": "/api/specific-resource"
  },
  "response": {
    "status": 200
  }
}
```

## Typical usage — catch-all fallback

A low-priority (high numeric) catch-all stub can serve as a customised default for unmapped requests, letting more specific stubs win.

```java
stubFor(any(anyUrl())
    .atPriority(10)
    .willReturn(aResponse()
        .withStatus(404)
        .withBody("{ \"status\": \"Error\", \"message\": \"Endpoint not found\" }")));
```

## Sources

- [Stubbing | WireMock](https://wiremock.org/docs/stubbing/)
