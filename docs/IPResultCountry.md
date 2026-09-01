# GeoAPI::IPResultCountry

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **iso_code** | **String** |  | [optional] |
| **name** | **String** |  | [optional] |
| **is_in_european_union** | **Boolean** |  | [optional] |

## Example

```ruby
require 'geoapi'

instance = GeoAPI::IPResultCountry.new(
  iso_code: US,
  name: United States,
  is_in_european_union: false
)
```

