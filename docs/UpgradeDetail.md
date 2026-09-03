# GeoSearch::UpgradeDetail

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **upgrade_url** | **String** | Absolute URL of the billing page where the plan can be raised. Derived server-side from configuration and never reflected from a request header or parameter. |  |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::UpgradeDetail.new(
  upgrade_url: https://geosearch.dev/dashboard#billing
)
```

