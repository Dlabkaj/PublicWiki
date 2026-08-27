# Custom Template Helpers

Extension point for adding user-defined Handlebars helpers to WireMock's response templating system.

## Extension interface

Extensions that implement the `TemplateHelperProviderExtension` interface provide additional Handlebars helpers to the templating system.

## Registration example

```java
new WireMockServer(wireMockConfig().extensions(
    new TemplateHelperProviderExtension() {
        @Override
        public String getName() {
            return "custom-helpers";
        }

        @Override
        public Map<String, Helper<?>> provideTemplateHelpers() {
            Helper<String> helper = (context, options) -> context.length();
            return Map.of("string-length", helper);
        }
    }
));
```

Key methods on the interface:

- `getName()` — returns the extension name (`"custom-helpers"` in the example).
- `provideTemplateHelpers()` — returns a `Map<String, Helper<?>>` keyed by the helper name used in templates.

## Using the registered helper

A helper registered under `string-length` is invoked in a template like this:

```
{{string-length 'abcde'}}
{{string-length request.body}}
```

## Sources

- [Adding Template Helpers | WireMock](https://wiremock.org/docs/extensibility/adding-template-helpers/)
