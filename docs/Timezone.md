# GeoSearch::Timezone

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **country_code** | **String** |  | [optional] |
| **timezone_id** | **String** |  | [optional] |
| **gmt_offset** | **Float** |  | [optional] |
| **dst_offset** | **Float** |  | [optional] |
| **raw_offset** | **Float** |  | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::Timezone.new(
  id: null,
  country_code: US,
  timezone_id: America/New_York,
  gmt_offset: -5.0,
  dst_offset: -4.0,
  raw_offset: -5.0
)
```

