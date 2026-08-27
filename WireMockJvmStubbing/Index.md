# WireMock JVM stubbing patterns

Landing page for **WireMock JVM stubbing patterns**. Sub-pages:

- [CustomMatching](CustomMatching.md) — Extension point for supplying request-matching logic beyond WireMock's standard matchers.
- [CustomTemplateHelpers](CustomTemplateHelpers.md) — Extension point for adding user-defined Handlebars helpers to WireMock's response templating system.
- [RequestMatching](RequestMatching.md) — WireMock matches incoming requests against stubs using rich per-attribute predicates.
- [ResponseTemplating](ResponseTemplating.md) — Response headers, bodies, and proxy URLs in WireMock JVM can be rendered using Handlebars templates, enabling request…
- [Scenarios](Scenarios.md) — State-machine gating for stubs — a stub can require a named scenario be in a specific state before it matches, and can…
- [StubPriority](StubPriority.md) — Numeric attribute controlling which stub wins when a request matches more than one mapping.
