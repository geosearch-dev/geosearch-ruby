# GeoAPI::ErrorResponseError

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **code** | **String** |  |  |
| **message** | **String** |  |  |
| **details** | [**Array&lt;ErrorResponseErrorDetailsInner&gt;**](ErrorResponseErrorDetailsInner.md) |  | [optional] |
| **request_id** | **String** | Correlation identifier present on every error response. Quote this when contacting support. |  |
| **trace_id** | **String** | W3C trace ID of the distributed trace for this request, when tracing is enabled. Omitted entirely when no span was recording, so clients must treat it as optional. It complements rather than replaces &#x60;request_id&#x60;. | [optional] |
| **quota** | [**QuotaDetail**](QuotaDetail.md) |  | [optional] |
| **upgrade** | [**UpgradeDetail**](UpgradeDetail.md) |  | [optional] |

## Example

```ruby
require 'geoapi'

instance = GeoAPI::ErrorResponseError.new(
  code: not_found,
  message: The requested resource was not found,
  details: null,
  request_id: req_abc123,
  trace_id: 4bf92f3577b34da6a3ce929d0e0e4736,
  quota: null,
  upgrade: null
)
```

