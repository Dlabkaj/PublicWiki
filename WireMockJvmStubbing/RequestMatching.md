# Request Matching

WireMock matches incoming requests against stubs using rich per-attribute predicates. Matchable request attributes: URL, HTTP method, query parameters, form parameters, headers, basic auth, cookies, request body, multipart/form-data, and client IP. Client-IP matching is available from WireMock 3.13.0.

Source: [Request Matching | WireMock](https://wiremock.org/docs/request-matching/)

## URL matching

Four URL matcher variants, choosing (a) equality vs regex and (b) full URL (path+query) vs path only:

- `urlEqualTo(...)` — equality on path and query
- `urlMatching(...)` — regex on path and query
- `urlPathEqualTo(...)` — equality on path only
- `urlPathMatching(...)` — regex on path only

Matching on the path only is preferable when multiple query parameters need to match in an order-invariant manner.

### Path templates

From WireMock 3.0.0 onward, `urlPathTemplate(...)` matches URLs against an RFC 6570 path template. Path templates enable matching path variables the same way as query params/headers via `withPathParam(name, matcher)`, and let path variables be referenced by name in response templates.

## Attribute-value predicates

Applied to headers, cookies, query/form/path params, and body via `.withHeader`, `.withCookie`, `.withQueryParam`, `.withFormParam`, `.withPathParam`, `.withRequestBody`:

| Predicate | Semantics |
|---|---|
| `equalTo(v)` | entire value equals expected |
| `equalToIgnoreCase(v)` | equality, case-insensitive |
| `binaryEqualTo(bytes)` / `binaryEqualTo(base64)` | byte-array equality; base64 accepted |
| `containing(v)` | substring match |
| `notContaining(v)` | negative substring |
| `matching(regex)` | entire value matches regex |
| `notMatching(regex)` | negative regex |
| `absent()` | attribute is absent from the request |

### JSON body

- `equalToJson(json)` — semantic JSON equality. Two boolean flags relax it: `ignoreArrayOrder`, `ignoreExtraElements` (JSON keys `ignoreArrayOrder`, `ignoreExtraElements`).
- JSON equality is implemented via JsonUnit and supports JsonUnit placeholders (e.g. `${json-unit.any-string}`) as wildcards.
- `matchingJsonPath(expr)` — matches if the JSONPath expression returns a non-null single value or a non-empty object/array. Sub-forms: presence, equality (via filter expr), regex (via filter expr), size (via `size()` filter), and nested-value matching where the JSONPath result is passed to another matcher.
- Since JSONPath results are coerced to string, a selected sub-document can be re-matched with `equalToJson`.
- `matchingJsonSchema(schema)` — validates the body against a JSON Schema. Default draft is `V202012`; overridable via `schemaVersion` to one of `V4`, `V6`, `V7`, `V201909`, `V202012`. JSON stub form is supported in WireMock 3.4+.

### XML body

- `equalToXml(xml)` — semantic XML equality, backed by XMLUnit.
- Supports XMLUnit placeholders (`${xmlunit.ignore}`, custom delimiter regexes via `placeholderOpeningDelimiterRegex` / `placeholderClosingDelimiterRegex`).
- `exemptingComparisons(...)` disables specific XMLUnit comparison types; defaults include `ELEMENT_TAG_NAME`, `SCHEMA_LOCATION`, `NO_NAMESPACE_SCHEMA_LOCATION`, `NODE_TYPE`, `NAMESPACE_PREFIX`, `NAMESPACE_URI`, `TEXT_VALUE`, `PROCESSING_INSTRUCTION_TARGET`, `PROCESSING_INSTRUCTION_DATA`, `ELEMENT_NUM_ATTRIBUTES`, `ATTR_VALUE`, `CHILD_NODELIST_LENGTH`, `CHILD_LOOKUP`, `ATTR_NAME_LOOKUP`.
- From WireMock 3.7.0, an extra argument enables `ignoreOrderOfSameNode` so identical child nodes need not be ordered.
- From WireMock 3.12.0, `namespaceAwareness` accepts `STRICT`, `NONE`, or `LEGACY`; `LEGACY` is discouraged.
- `matchingXPath(expr)` — matches if the XPath returns any element. Uses Java's built-in XPath (via XMLUnit); through at least Java 8 this is XPath 1.0. Can declare namespaces via `.withXPathNamespace(prefix, uri)`. Nested-value form: `matchingXPath(expr, innerMatcher)` re-matches the XPath result.

### Dates and times

Three date operators — `before`, `after`, `equalToDateTime` — parameterised identically.

- Expected value may be literal (e.g. `"2021-05-01T00:00:00Z"`, or a `ZonedDateTime`/`LocalDateTime`) or an offset from now (`"now +3 days"`, or `beforeNow().expectedOffset(3, DateTimeUnit.DAYS)`).
- Zoned vs local: if expected is zoned and actual is local, the actual assumes system timezone; if expected is local and actual is zoned, the actual's zone is stripped before comparison.
- Default parsers cover ISO 8601 plus HTTP RFCs 1123, 1036 and asctime. Custom formats set via `.actualFormat(pattern)` using Java date format strings.
- Both expected and actual may be truncated: `first minute of hour`, `first hour of day`, `first day of month`, `first day of next month`, `last day of month`, `first day of year`, `first day of next year`, `last day of year`.
- Truncation is applied before offset by default; set `applyTruncationLast: true` to reverse the order.

### Numbers

`equalToNumber`, `greaterThanNumber`, `greaterThanEqualNumber`, `lessThanNumber`, `lessThanEqualNumber` compare by numeric value; non-parseable inputs never match.

## Multipart

`withMultipartRequestBody(aMultipart()...)` — each multipart pattern is itself a mini-HTTP-request with headers + bodyPatterns. `matchingType` is `ANY` (default) or `ALL`, controlling whether any/all request parts must match the pattern.

## Basic authentication

`.withBasicAuth(username, password)` is a shorthand for the corresponding encoded `Authorization` header.

## Combining predicates

- Logical AND: `and(a, b, ...)` or fluent `a.and(b)`.
- Logical OR: `or(a, b, ...)` or fluent `a.or(b)`.
- Logical NOT: `not(matcher)`.
- Date-range example: combine `matchingJsonPath("$.date", before(X).and(after(Y)))` to bound a JSON field between two dates.

## Multi-value headers / query params

For attributes with multiple values:

- `havingExactly(v1, v2, v3)` — exact multi-value match; the attribute must have exactly those values and no others. Accepts either string literals or nested matchers (e.g. `equalTo`, `containing`, `notContaining`).
- `including(v1, v2, v3)` — required subset; other values may also be present. Also accepts nested matchers.

## Custom matching

Custom matching logic can be plugged in when in-built operators are insufficient.

## Open questions

- Stub priority ordering is not addressed by this source; expected in the dedicated Stubbing page.
- Response templating is only referenced in passing (path-variable interpolation); details expected in the Response Templating page.
