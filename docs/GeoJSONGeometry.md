# GeoSearch::GeoJSONGeometry

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **type** | **String** | &#x60;MultiPolygon&#x60; for most areas, &#x60;Polygon&#x60; for areas with a single ring — including areas that BECOME single-ring under &#x60;?simplify&#x3D;&#x60;. Do not pin this to one value. |  |
| **coordinates** | **Array&lt;Object&gt;** | Nesting depth depends on &#x60;type&#x60;: three levels for &#x60;Polygon&#x60;, four for &#x60;MultiPolygon&#x60;. Positions are &#x60;[longitude, latitude]&#x60; in EPSG:4326, per the GeoJSON specification. |  |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::GeoJSONGeometry.new(
  type: MultiPolygon,
  coordinates: [[[[-124.7, 48.4], [-124.6, 48.4], [-124.6, 48.3], [-124.7, 48.4]]]]
)
```

