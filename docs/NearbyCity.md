# GeoSearch::NearbyCity

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **name** | **String** |  | [optional] |
| **country_code** | **String** |  | [optional] |
| **population** | **Integer** |  | [optional] |
| **timezone** | **String** |  | [optional] |
| **latitude** | **Float** |  | [optional] |
| **longitude** | **Float** |  | [optional] |
| **distance_km** | **Float** |  | [optional] |
| **country** | [**CountryRef**](CountryRef.md) |  | [optional] |
| **region** | [**RegionRef**](RegionRef.md) |  | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::NearbyCity.new(
  id: 5391959,
  name: San Francisco,
  country_code: US,
  population: 873965,
  timezone: America/Los_Angeles,
  latitude: 37.77493,
  longitude: -122.41942,
  distance_km: 12.5,
  country: null,
  region: null
)
```

