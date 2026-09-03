# GeoSearch::Boundary

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **geoname_id** | **Integer** | The area the polygon belongs to, read back from the source row rather than echoed from the request. |  |
| **name** | **String** | The area&#39;s name, resolved through &#x60;?lang&#x3D;&#x60; when supplied. |  |
| **type** | **String** | Which kind of area this is. |  |
| **geometry** | [**GeoJSONGeometry**](GeoJSONGeometry.md) |  |  |
| **simplify** | **Float** | The tolerance that was ACTUALLY APPLIED, or &#x60;null&#x60; for full precision.  THIS IS NOT YOUR &#x60;?simplify&#x3D;&#x60; ECHOED BACK. A requested tolerance of &#x60;0&#x60; is dropped rather than executed, so &#x60;?simplify&#x3D;0&#x60; returns &#x60;null&#x60; here — that is the truthful answer, because no simplification was performed. Read this field rather than assuming the request was honoured verbatim. |  |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::Boundary.new(
  geoname_id: 6252001,
  name: United States,
  type: country,
  geometry: null,
  simplify: null
)
```

