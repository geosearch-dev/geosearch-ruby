# GeoAPI::AutocompleteResult

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **name** | **String** |  | [optional] |
| **type** | **String** |  | [optional] |
| **country_code** | **String** |  | [optional] |
| **population** | **Integer** |  | [optional] |

## Example

```ruby
require 'geoapi'

instance = GeoAPI::AutocompleteResult.new(
  id: 5391959,
  name: San Francisco,
  type: city,
  country_code: US,
  population: 873965
)
```

