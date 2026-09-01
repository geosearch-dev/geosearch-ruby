# GeoAPI::GetStatus200ResponseData

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **status** | **String** |  | [optional] |
| **database** | **String** |  | [optional] |

## Example

```ruby
require 'geoapi'

instance = GeoAPI::GetStatus200ResponseData.new(
  status: healthy,
  database: connected
)
```

