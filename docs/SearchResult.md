# GeoSearch::SearchResult

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **type** | **String** |  | [optional] |
| **id** | **Integer** |  | [optional] |
| **name** | **String** |  | [optional] |
| **rank** | **Float** |  | [optional] |
| **country** | **String** |  | [optional] |
| **population** | **Integer** |  | [optional] |
| **latitude** | **Float** |  | [optional] |
| **longitude** | **Float** |  | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::SearchResult.new(
  type: city,
  id: 5391959,
  name: San Francisco,
  rank: 0.95,
  country: US,
  population: 873965,
  latitude: 37.77493,
  longitude: -122.41942
)
```

