# GeoAPI::RegionRef

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **name** | **String** |  | [optional] |
| **admin_code** | **String** |  | [optional] |

## Example

```ruby
require 'geoapi'

instance = GeoAPI::RegionRef.new(
  id: 5332921,
  name: California,
  admin_code: CA
)
```

