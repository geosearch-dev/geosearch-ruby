# GeoAPI::ReverseGeocodeResult

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **city** | [**NearbyCity**](NearbyCity.md) |  | [optional] |
| **distance_km** | **Float** |  | [optional] |

## Example

```ruby
require 'geoapi'

instance = GeoAPI::ReverseGeocodeResult.new(
  city: null,
  distance_km: 0.3
)
```

