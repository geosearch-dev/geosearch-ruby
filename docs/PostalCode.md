# GeoSearch::PostalCode

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **country_code** | **String** |  | [optional] |
| **postal_code** | **String** |  | [optional] |
| **place_name** | **String** |  | [optional] |
| **admin_name1** | **String** |  | [optional] |
| **admin_code1** | **String** |  | [optional] |
| **admin_name2** | **String** |  | [optional] |
| **admin_code2** | **String** |  | [optional] |
| **admin_name3** | **String** | Third-level administrative area. Empty where the source data defines none — most US rows, including this example. | [optional] |
| **admin_code3** | **String** | Third-level administrative code. Empty where the source data defines none — most US rows, including this example. | [optional] |
| **latitude** | **Float** |  | [optional] |
| **longitude** | **Float** |  | [optional] |
| **accuracy** | **Integer** |  | [optional] |
| **country** | [**CountryRef**](CountryRef.md) |  | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::PostalCode.new(
  id: 1140425,
  country_code: US,
  postal_code: 94105,
  place_name: San Francisco,
  admin_name1: California,
  admin_code1: CA,
  admin_name2: San Francisco,
  admin_code2: 075,
  admin_name3: ,
  admin_code3: ,
  latitude: 37.7864,
  longitude: -122.3892,
  accuracy: 4,
  country: null
)
```

