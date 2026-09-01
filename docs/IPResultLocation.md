# GeoAPI::IPResultLocation

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **latitude** | **Float** |  | [optional] |
| **longitude** | **Float** |  | [optional] |
| **accuracy_radius** | **Integer** |  | [optional] |
| **timezone** | **String** |  | [optional] |

## Example

```ruby
require 'geoapi'

instance = GeoAPI::IPResultLocation.new(
  latitude: 37.386,
  longitude: -122.0838,
  accuracy_radius: 1000,
  timezone: America/Los_Angeles
)
```

