# GeoAPI::CountryRef

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **iso_code** | **String** |  | [optional] |
| **name** | **String** |  | [optional] |

## Example

```ruby
require 'geoapi'

instance = GeoAPI::CountryRef.new(
  iso_code: US,
  name: United States
)
```

