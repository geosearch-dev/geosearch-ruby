# GeoSearch::Region

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** |  | [optional] |
| **geoname_id** | **Integer** |  | [optional] |
| **country_code** | **String** |  | [optional] |
| **admin_code** | **String** |  | [optional] |
| **name** | **String** |  | [optional] |
| **ascii_name** | **String** |  | [optional] |
| **level** | **Integer** |  | [optional] |
| **parent_geoname_id** | **Integer** |  | [optional] |
| **population** | **Integer** |  | [optional] |
| **latitude** | **Float** |  | [optional] |
| **longitude** | **Float** |  | [optional] |
| **country** | [**CountryRef**](CountryRef.md) |  | [optional] |
| **geometry** | [**GeoJSONMultiPolygon**](GeoJSONMultiPolygon.md) | Region boundary. Returned by default on &#x60;GET /v1/regions/{id}&#x60;, and on request via &#x60;?fields&#x3D;geometry&#x60; on &#x60;GET /v1/regions&#x60; and &#x60;GET /v1/countries/{code}/regions&#x60;.  REQUIRES A PAID PLAN. On all three of those routes this key is OMITTED ENTIRELY for a Free-tier key — absent, not null, with a 200 status and no error. A client reading &#x60;data.geometry.type&#x60; unconditionally will fail on a null dereference.  To be told explicitly rather than silently, request the polygon from &#x60;GET /v1/boundaries/{geoname_id}&#x60;, which answers a Free key with a 403 and an upgrade link. | [optional] |

## Example

```ruby
require 'geosearch'

instance = GeoSearch::Region.new(
  id: 5332921,
  geoname_id: 5332921,
  country_code: US,
  admin_code: CA,
  name: California,
  ascii_name: California,
  level: 1,
  parent_geoname_id: 6252001,
  population: 39538223,
  latitude: 36.778,
  longitude: -119.418,
  country: null,
  geometry: null
)
```

