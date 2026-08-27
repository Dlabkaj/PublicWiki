# Response Templating

Response headers, bodies, and proxy URLs in WireMock JVM can be rendered using
Handlebars templates, enabling request attributes to be used when generating the
response.

## Enabling and disabling

- Response templating is enabled by default in local mode when WireMock is started
 programmatically, but only applies to stubs that explicitly declare the
 `response-template` transformer.
- Global templating (all stubs, no per-stub declaration) is switched on via the
 `globalTemplating(true)` startup option
 (`new WireMockServer(options().globalTemplating(true))`).
- Templating can be disabled entirely with `templatingEnabled(false)` on startup
 options.
- On a stub using `bodyFileName`, templating of that body file can be disabled per
 stub with `disableBodyFileTemplating: true` inside `transformerParameters` in the
 response definition.

## Applying to a stub (local mode)

`response-template` is added to the response transformers list. Java:

```
wm.stubFor(get(urlPathEqualTo("/templated"))
.willReturn(aResponse()
.withBody("{{request.path.[0]}}")
.withTransformers("response-template")));
```

JSON: `"transformers": ["response-template"]` alongside the templated `body`.

Templating also applies to proxy URLs (`proxiedFrom` / `proxyBaseUrl`) and to the
selected body file path via `withBodyFile("files/{{request.pathSegments.[1]}}")`.

## Template caching

All templated fragments (headers, bodies, proxy URLs) are cached in compiled form
because compilation is expensive for larger templates. Cache capacity
is unlimited by default and can be capped via
`options().withMaxTemplateCacheEntries(10000)`.

## Request model

Request attributes exposed to templates:

- `request.id` — unique ID per request (WireMock 3.7.0)
- `request.url` — URL path and query
- `request.path` — URL path; also indexable (`request.path.3`); path-template
 matches expose named variables (`request.path.contactId`)
- `request.pathSegments.[<n>]` — zero-indexed path segments
- `request.query.<key>` — first value of query parameter; `request.query.<key>.[<n>]`
 for nth
- `request.method`, `request.host`, `request.port`, `request.scheme`, `request.baseUrl`
- `request.headers.<key>` — first value; `request.headers.[<key>]` for keys with
 awkward characters; `request.headers.<key>.[<n>]` for nth
- `request.cookies.<key>` and `request.cookies.<key>.[<n>]`
- `request.body` (avoid for non-text bodies)
- `request.bodyAsBase64` (WireMock 3.8.0)
- `request.multipart` — boolean (WireMock 3.8.0)
- `request.parts` — multipart parts by name (WireMock 3.8.0); each part exposes
 `.binary`, `.headers.<key>`, `.body`, `.bodyAsBase64`

### One-or-many values

Query, form, and header values wrap in a "list or single" type. Without an index it
returns the first value; index access is supported.

For `/multi-query?things=1&things=2&things=3`:

- `{{request.query.things}}` → `1`
- `{{request.query.things.0}}` / `{{request.query.things.first}}` → `1`
- `{{request.query.things.[-1]}}` → `2`
- `{{request.query.things.last}}` → `3`

Note: with the `eq` helper the indexed form is required, because the non-indexed
form returns the wrapper type rather than a String.

### Keys with special characters

Handlebars reserves certain characters, so the `lookup` helper is used to reference
keys containing them, e.g. array-style query params
`{{lookup request.query 'ids[].1'}}` for URL `?ids[]=111&ids[]=222&ids[]=333`.

## Transformer parameters

Arbitrary values can be passed via `withTransformerParameter(name, value)` (Java)
or a `transformerParameters` object (JSON) and are referenced with the
`parameters.` prefix, e.g. `{{parameters.MyCustomParameter}}`.

## Handlebars helpers

All standard helpers from the jknack Java Handlebars implementation, plus its
string helpers and conditional helpers, are available (e.g.
`{{capitalize request.query.search}}`).

### Number and assignment helpers

`#assign`, `isOdd`, `isEven`, `stripes` (alternating class output).

### `val` helper (WireMock 3.6.0)

Accesses a value or a default; can also assign to a variable. Unlike `assign`, `val`
maintains the type of the value being assigned.

- `{{val request.query.search or='default'}}`
- `{{val request.query.search default='default'}}`
- `{{val request.query.search assign='myVar'}}`

### XPath helpers

- `xPath request.body '/outer/inner/text()'` extracts text; `xPath` returning the
 element node prints the element.
- `soapXPath` is a convenience for SOAP bodies (paths are relative to the SOAP body
 contents, e.g. `/a/test/text()` for the payload).
- Since version 2.27.0 the XPath helper returns collections of node objects rather
 than a single string, so results can be piped into further helpers.
- Node objects expose `name`, `text`, `attributes` (name→value map); referring to
 the node itself prints it. Iterate with `#each`.

### `formatXml` helper (WireMock 3.10.0)

Rewrites input XML with format options `compact` (whitespace removed) or `pretty`
(default; newlines and indentation).

### JSON helpers

- `jsonPath request.body '$.outer.inner'` extracts values or sub-documents; a
 `default=` parameter is applied when the path evaluates to null/undefined.
- `parseJson` parses input into a map-of-maps, either as a block with a variable
 name (`{{#parseJson 'parsedObj'}}...{{/parseJson}}`) or as a parameter
 (`{{parseJson request.body 'bodyJson'}}`).
- `toJson` (WireMock 3.10.0) converts any object into a JSON string.
- `formatJson` (WireMock 3.10.0) with format options `compact` and `pretty` (default).
- `jsonArrayAdd` (WireMock 3.10.0) appends an element to a JSON array; parameters
 include `maxItems` (drops from the front to hold size), `flatten=true` (merge a
 new array into the existing one instead of nesting it), and `jsonPath=` (append
 to a nested array by path).
- `jsonMerge` (WireMock 3.10.0) merges two JSON objects; recurses into common
 object-typed keys but overwrites array-typed values with the second object's
 value. `removeNulls=true` (WireMock 3.12.0) strips keys whose
 value in the second document is null.
- `jsonRemove` (WireMock 3.10.0) removes an element from a JSON array or a key
 from a JSON object using a JSONPath expression.
- `jsonSort` (WireMock 4.0.0-beta.21) sorts a JSON array by a JSONPath field; sort
 values must all be of the same comparable type (Number, String, Boolean); `order`
 is `asc` by default and may be `desc`; `nulls` may be `first` (default) or `last`;
 missing fields are treated as null; sort is stable (order of equal values
 preserved).

### Date and time helpers

- `now` prints the current time; supports `offset` (e.g. `'3 days'`, `'-24 seconds'`,
 `'1 years'`), `timezone` (default UTC), and `format` (Java `SimpleDateFormat`).
- `format='epoch'` renders UNIX epoch time in milliseconds; `format='unix'` renders
 UNIX time in seconds.
- `parseDate` parses a date, defaulting to ISO8601, RFC 1123, RFC 1036 and ASCTIME
 formats, with custom `format=` accepted (including `unix` and `epoch`).
- `truncateDate` truncates a parsed date (e.g. `'first day of month'`).

### Random and pick helpers

- `randomValue` — `length`, `type` (`ALPHANUMERIC`, `ALPHABETIC`, `NUMERIC`,
 `ALPHANUMERIC_AND_SYMBOLS`, `UUID`, `HEXADECIMAL`), `uppercase`.
- `pickRandom` — literal list or array parameter; `count=N` returns a list of N
 unique picks instead of a single value.
- `randomInt` and `randomDecimal` — optional `lower` / `upper` bounds; both return
 actual typed numbers usable in arithmetic.

### `numberFormat` helper

Predefined formats: `integer`, `currency`, `percent` (locale-affected).
A custom format string (Java `DecimalFormat`) is also accepted:
`{{{numberFormat 123.4567 '###.000000' 'en_GB'}}}` → `123.456700`.

Digit bounds: `maximumFractionDigits`, `minimumFractionDigits`,
`maximumIntegerDigits`, `minimumIntegerDigits`.

`groupingUsed=false` disables locale-based digit grouping.

`roundingMode`: `up`, `down`, `half_up`, `half_down`, `half_even`, `ceiling`,
`floor` (see Java `RoundingMode`).

### Fake data helper

`random 'Name.first_name'` returns fake data from the Data Faker library; supplied
by `RandomExtension` due to library size.

### Arithmetic and collection helpers

- `math` — `+`, `-`, `*`, `/`, `%`; accepts integers, decimals or strings; always
 yields a number.
- `range 3 8` — array of integers between the bounds.
- `array` — array literal from parameters; no params yields empty array.
- `arrayAdd` / `arrayRemove` (WireMock 3.6.0) — `position` accepts an integer or
 `start` / `end`; default position is end.
- `arrayJoin` (WireMock 3.6.0) — concatenates values with a separator; optional
 `prefix` and `suffix`; also works as a block helper iterating with `as |item|`.

### String / matching helpers

- `contains` — boolean membership test on a string or array; usable inside `#if` or
 as a block.
- `matches` — boolean regex test; usable inside `#if` or as a block.
- `trim` — removes leading/trailing whitespace.
- `base64` — encode or decode (with `decode=true`); `padding=false` for unpadded
 encoding.
- `urlEncode` — URL-encode or decode (with `decode=true`).
- `formData` — parses input as HTTP form into a named variable exposing fields as
 attributes; optional `urlDecode=true`; multi-valued fields accessible by index or
 `first` / `last`.
- `regexExtract` — extract a single match or, with groups, an object of parts
 assigned to a named variable; `default=` returns a default when there is no match
 (without a default, no match throws).
- `size` — size of a string, list, or map.

### Environment helpers

- `hostname` — the local machine's hostname.
- `systemValue` — reads environment variables or system properties; parameters
 `type` (defaults to `ENVIRONMENT`, alternatively `PROPERTY`), `key`, and (from
 WireMock 3.5) `default`.
- Permitted system-key patterns can be extended by constructing the
 `ResponseTemplateTransformer` directly; regex matching is case-insensitive; when
 no patterns are set the default is `wiremock.*`.

## Extending the engine

Custom Handlebars helpers register via extension point (see "Adding Template
Helpers"); custom template model data providers register similarly (see "Adding
Template Model Data").

The `ResponseTemplateTransformer` constructor takes four arguments:

1. The `TemplateEngine`.
2. Whether templating applies globally.
3. A `FileSource` — files used for relative references in stub definitions.
4. A list of `TemplateModelDataProviderExtension` objects providing additional
 metadata injected into the model.

## Sources

- WireMock docs — Response Templating. <https://wiremock.org/docs/response-templating/>
