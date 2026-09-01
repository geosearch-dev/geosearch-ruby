# GeoAPI::BoundariesApi

All URIs are relative to *https://geosearch.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_boundary**](BoundariesApi.md#get_boundary) | **GET** /v1/boundaries/{geoname_id} | Fetch an area&#39;s boundary polygon as GeoJSON |


## get_boundary

> <BoundarySingleResponse> get_boundary(geoname_id, opts)

Fetch an area's boundary polygon as GeoJSON

Returns the boundary polygon for one country or region as a bare GeoJSON geometry.  ## COSTS 5 QUOTA UNITS  This endpoint charges five units against the monthly quota, not one. The premium is priced on PAYLOAD rather than on query time: country GeoJSON averages 62.6 KB and reaches 1.9 MB, and region GeoJSON reaches 2.8 MB — two to three orders of magnitude above an ordinary list response.  `?simplify=` does NOT reduce the cost. It trades server CPU for client bytes (simplification measures 209–248 ms against 10.3 ms for the plain fetch), so the route is expensive to serve either way.  REJECTIONS COST ONE UNIT, NOT FIVE. A 400, a 422, either 404 and the 403 below all charge the standard single unit, so probing which ids are fetchable — and bouncing off the paywall — is not billed at the premium rate. Only a request that actually reaches the polygon fetch is charged five, including one that reaches it and then times out.  ## Plan requirements  REGION boundaries require a paid plan. COUNTRY boundaries are available on every plan, including Free. A Free key requesting a region boundary receives a 403 `tier_upgrade_required` carrying an upgrade link — a visible refusal, not a silent omission.  This is the same split the `geometry` field follows on the country and region endpoints, with one deliberate difference: there the field is simply absent from a 200, while here the refusal is explicit and tells you what to do about it.  ## Response shape  `data.geometry` is a BARE GeoJSON geometry — the `{\"type\": ..., \"coordinates\": ...}` object — and NOT a GeoJSON `Feature`. There is no `properties` wrapper; the three sibling fields carry that information. This matches the geometry `/v1/countries/{code}` and `/v1/regions/{id}` already return.  `type` is `Polygon` OR `MultiPolygon`. Do not pin it: applying `?simplify=` can collapse a MultiPolygon into a Polygon for areas whose smaller parts disappear at the requested tolerance.  `?fields=` IS NOT SUPPORTED on this endpoint and is ignored if sent. Field selection here works by serialising the whole object and then dropping keys, so `?fields=name` on a 1.9 MB polygon would build the polygon in full and discard it — strictly more expensive than not sending the parameter. Callers who want only the name should use `/v1/countries/{code}` or `/v1/regions/{id}`. 

### Examples

```ruby
require 'time'
require 'geoapi'
# setup authorization
GeoAPI.configure do |config|
  # Configure API key authorization: apiKeyAuth
  config.api_key['X-API-Key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-API-Key'] = 'Bearer'
end

api_instance = GeoAPI::BoundariesApi.new
geoname_id = 6252001 # Integer | GeoNames id of a country or a region. A city id — or any id that does not name an area — is a 404 `area_not_an_area`, not a 400.
opts = {
  simplify: 0.01, # Float | Douglas-Peucker tolerance in EPSG:4326 DEGREES, applied before the polygon is serialised. Omit it for full precision.  DEGREES, NOT METRES. The upper bound of 10 is roughly 1,100 km, chosen to make the unit obviously wrong to anyone who typed a value in metres. Simplification stops changing the shape above about 1 degree, so values beyond that buy nothing.  `0` is accepted and is a no-op: the response reports `simplify: null`, because no tolerance was actually applied.  A negative, non-finite or out-of-range value is a 422, never a 500.  SUPPLY IT AT MOST ONCE. `?simplify=0.01&simplify=0.5` is a 422 rather than a request served with one of the two values silently dropped: two tolerances are two conflicting instructions, and the server does not guess which was meant.
  lang: 'de' # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
}

begin
  # Fetch an area's boundary polygon as GeoJSON
  result = api_instance.get_boundary(geoname_id, opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling BoundariesApi->get_boundary: #{e}"
end
```

#### Using the get_boundary_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<BoundarySingleResponse>, Integer, Hash)> get_boundary_with_http_info(geoname_id, opts)

```ruby
begin
  # Fetch an area's boundary polygon as GeoJSON
  data, status_code, headers = api_instance.get_boundary_with_http_info(geoname_id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <BoundarySingleResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling BoundariesApi->get_boundary_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **geoname_id** | **Integer** | GeoNames id of a country or a region. A city id — or any id that does not name an area — is a 404 &#x60;area_not_an_area&#x60;, not a 400. |  |
| **simplify** | **Float** | Douglas-Peucker tolerance in EPSG:4326 DEGREES, applied before the polygon is serialised. Omit it for full precision.  DEGREES, NOT METRES. The upper bound of 10 is roughly 1,100 km, chosen to make the unit obviously wrong to anyone who typed a value in metres. Simplification stops changing the shape above about 1 degree, so values beyond that buy nothing.  &#x60;0&#x60; is accepted and is a no-op: the response reports &#x60;simplify: null&#x60;, because no tolerance was actually applied.  A negative, non-finite or out-of-range value is a 422, never a 500.  SUPPLY IT AT MOST ONCE. &#x60;?simplify&#x3D;0.01&amp;simplify&#x3D;0.5&#x60; is a 422 rather than a request served with one of the two values silently dropped: two tolerances are two conflicting instructions, and the server does not guess which was meant. | [optional] |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |

### Return type

[**BoundarySingleResponse**](BoundarySingleResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

