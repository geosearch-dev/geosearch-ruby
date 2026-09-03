# GeoSearch::BatchRequest

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **ids** | **Array&lt;Integer&gt;** | Array of entity IDs to look up (max 50) |  |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::BatchRequest.new(
  ids: [5391959, 5128581, 4887398]
)
```

