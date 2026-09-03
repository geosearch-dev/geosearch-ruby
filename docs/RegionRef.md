# GeoSearch::RegionRef

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **name** | **String** |  | [optional] |
| **admin_code** | **String** |  | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::RegionRef.new(
  id: 5332921,
  name: California,
  admin_code: CA
)
```

