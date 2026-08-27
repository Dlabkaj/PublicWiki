# Scenarios

State-machine gating for stubs — a stub can require a named scenario be in a specific state before it matches, and can transition the scenario to a new state as a side-effect of the request.

## Model

- A scenario is a state machine whose states can be arbitrarily assigned.
- Its starting state is always `Scenario.STARTED` (JSON: `"Started"`).
- Stub mappings can be configured to match on scenario state, so stub A can be returned initially, then stub B once the next scenario state has been triggered.

## Java DSL — matching + transition

```java
stubFor(get(urlEqualTo("/todo/items")).inScenario("To do list")
.whenScenarioStateIs(STARTED)
.willReturn(aResponse().withBody("<items><item>Buy milk</item></items>")));

stubFor(post(urlEqualTo("/todo/items")).inScenario("To do list")
.whenScenarioStateIs(STARTED)
.withRequestBody(containing("Cancel newspaper subscription"))
.willReturn(aResponse().withStatus(201))
.willSetStateTo("Cancel newspaper item added"));
```

Key builder methods: `.inScenario(name)`, `.whenScenarioStateIs(state)`, `.willSetStateTo(state)`.

## JSON equivalent

```json
{
 "scenarioName": "To do list",
 "requiredScenarioState": "Started",
 "newScenarioState": "Cancel newspaper item added",
 "request": { "method": "POST", "url": "/todo/items"},
 "response": { "status": 201}}
```

Fields: `scenarioName`, `requiredScenarioState`, `newScenarioState`.

## Admin operations

| Operation | Java | HTTP |
|-----------|------|------|
| List scenarios | `getAllScenarios()` | `GET /__admin/scenarios` |
| Reset all | `WireMock.resetAllScenarios()` | `POST /__admin/scenarios/reset` |
| Reset one | `WireMock.resetScenario("name")` | `PUT /__admin/scenarios/{name}/state` (empty body) |
| Set state | `WireMock.setScenarioState("name", "state_2")` | `PUT /__admin/scenarios/{name}/state` with `{ "state": "state_2"}` |

`GET /__admin/scenarios` returns each scenario's `id`, `name`, current `state`, and `possibleStates`.

## Sources

- [Stateful Behaviour | WireMock](https://wiremock.org/docs/stateful-behaviour/)
