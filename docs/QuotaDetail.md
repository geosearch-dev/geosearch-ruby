# GeoSearch::QuotaDetail

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **limit** | **Integer** | Monthly request allowance for the account&#39;s current plan. |  |
| **used** | **Integer** | Requests consumed in the current quota period. |  |
| **resets_at** | **Time** | Start of the next quota period, when &#x60;used&#x60; returns to zero. Matches the &#x60;X-RateLimit-Reset&#x60; header on the same response, expressed as RFC 3339 rather than an epoch second. |  |
| **upgrade_url** | **String** | Absolute URL of the billing page where the plan can be raised. Derived server-side from configuration and never reflected from a request header or parameter. |  |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::QuotaDetail.new(
  limit: 2000000,
  used: 2000000,
  resets_at: 2026-03-01T00:00:00Z,
  upgrade_url: https://geosearch.dev/dashboard/billing
)
```

