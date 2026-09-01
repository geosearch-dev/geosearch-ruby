# GeoAPI::IPResult

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ip** | **String** |  | [optional] |
| **network** | **String** |  | [optional] |
| **continent** | [**IPResultContinent**](IPResultContinent.md) |  | [optional] |
| **country** | [**IPResultCountry**](IPResultCountry.md) |  | [optional] |
| **region** | [**IPResultRegion**](IPResultRegion.md) |  | [optional] |
| **city** | [**IPResultCity**](IPResultCity.md) |  | [optional] |
| **postal** | [**IPResultPostal**](IPResultPostal.md) |  | [optional] |
| **location** | [**IPResultLocation**](IPResultLocation.md) |  | [optional] |
| **is_anonymous_proxy** | **Boolean** |  | [optional] |
| **is_satellite_provider** | **Boolean** |  | [optional] |

## Example

```ruby
require 'geoapi'

instance = GeoAPI::IPResult.new(
  ip: 8.8.8.8,
  network: 8.8.8.0/24,
  continent: null,
  country: null,
  region: null,
  city: null,
  postal: null,
  location: null,
  is_anonymous_proxy: false,
  is_satellite_provider: false
)
```

