# GeoSearch::GeoJSONMultiPolygon

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **type** | **String** |  | [optional] |
| **coordinates** | **Array&lt;Array&lt;Array&lt;Array&lt;Float&gt;&gt;&gt;&gt;** |  | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::GeoJSONMultiPolygon.new(
  type: MultiPolygon,
  coordinates: [[[[-124.7, 48.4], [-124.6, 48.4], [-124.6, 48.3], [-124.7, 48.4]]]]
)
```

