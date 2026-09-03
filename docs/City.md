# GeoSearch::City

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **geoname_id** | **Integer** |  | [optional] |
| **name** | **String** |  | [optional] |
| **ascii_name** | **String** |  | [optional] |
| **country_code** | **String** |  | [optional] |
| **admin1_code** | **String** |  | [optional] |
| **admin2_code** | **String** |  | [optional] |
| **population** | **Integer** |  | [optional] |
| **elevation** | **Integer** |  | [optional] |
| **timezone** | **String** |  | [optional] |
| **latitude** | **Float** |  | [optional] |
| **longitude** | **Float** |  | [optional] |
| **country** | [**CountryRef**](CountryRef.md) |  | [optional] |
| **region** | [**RegionRef**](RegionRef.md) |  | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::City.new(
  id: 5391959,
  geoname_id: 5391959,
  name: San Francisco,
  ascii_name: San Francisco,
  country_code: US,
  admin1_code: CA,
  admin2_code: 075,
  population: 873965,
  elevation: 16,
  timezone: America/Los_Angeles,
  latitude: 37.77493,
  longitude: -122.41942,
  country: null,
  region: null
)
```

