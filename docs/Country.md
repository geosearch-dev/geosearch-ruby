# GeoSearch::Country

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **geoname_id** | **Integer** |  | [optional] |
| **iso_code** | **String** |  | [optional] |
| **iso3_code** | **String** |  | [optional] |
| **iso_numeric** | **Integer** |  | [optional] |
| **fips_code** | **String** |  | [optional] |
| **name** | **String** |  | [optional] |
| **capital** | **String** |  | [optional] |
| **area_sq_km** | **Float** |  | [optional] |
| **population** | **Integer** |  | [optional] |
| **continent_code** | **String** |  | [optional] |
| **tld** | **String** |  | [optional] |
| **currency_code** | **String** |  | [optional] |
| **currency_name** | **String** |  | [optional] |
| **phone** | **String** |  | [optional] |
| **postal_code_format** | **String** |  | [optional] |
| **postal_code_regex** | **String** |  | [optional] |
| **languages** | **Array&lt;String&gt;** |  | [optional] |
| **neighbours** | **Array&lt;String&gt;** |  | [optional] |
| **latitude** | **Float** |  | [optional] |
| **longitude** | **Float** |  | [optional] |
| **flag_emoji** | **String** |  | [optional] |
| **geometry** | [**GeoJSONMultiPolygon**](GeoJSONMultiPolygon.md) | Country boundary. Returned by default on &#x60;GET /v1/countries/{code}&#x60; and on request via &#x60;?fields&#x3D;geometry&#x60; on &#x60;GET /v1/countries&#x60;.  NOT TIER-GATED. Country geometry is served on every plan, including Free. Region geometry is gated — see the &#x60;Region&#x60; schema. | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::Country.new(
  id: 1,
  geoname_id: 6252001,
  iso_code: US,
  iso3_code: USA,
  iso_numeric: 840,
  fips_code: US,
  name: United States,
  capital: Washington,
  area_sq_km: 9833520.0,
  population: 331002651,
  continent_code: NA,
  tld: .us,
  currency_code: USD,
  currency_name: Dollar,
  phone: 1,
  postal_code_format: #####-####,
  postal_code_regex: ^\d{5}(-\d{4})?$,
  languages: [en-US, es-US],
  neighbours: [CA, MX],
  latitude: 39.76,
  longitude: -98.5,
  flag_emoji: null,
  geometry: null
)
```

