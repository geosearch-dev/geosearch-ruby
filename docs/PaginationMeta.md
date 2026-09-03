# GeoSearch::PaginationMeta

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **next_cursor** | **String** | Cursor for the next page | [optional] |
| **prev_cursor** | **String** | Cursor for the previous page | [optional] |
| **has_next** | **Boolean** |  | [optional] |
| **has_prev** | **Boolean** |  | [optional] |
| **count** | **Integer** | Number of items in this response | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::PaginationMeta.new(
  next_cursor: eyJpZCI6MjV9,
  prev_cursor: null,
  has_next: true,
  has_prev: false,
  count: 25
)
```

