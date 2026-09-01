# GeoAPI::PostalCodesApi

All URIs are relative to *https://geosearch.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**list_postal_codes**](PostalCodesApi.md#list_postal_codes) | **GET** /v1/postal-codes | List postal codes |
| [**nearest_postal_code**](PostalCodesApi.md#nearest_postal_code) | **GET** /v1/postal-codes/nearest | Find nearest postal codes |


## list_postal_codes

> <PostalCodeListResponse> list_postal_codes(opts)

List postal codes

Returns a paginated list of postal codes with optional filtering by country and code.

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

api_instance = GeoAPI::PostalCodesApi.new
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  country: 'US', # String | Filter by ISO alpha-2 country codes (comma-separated)
  code: '94105', # String | Filter by postal code
  within: 6252001, # Integer | Return only results whose coordinates fall geometrically inside the boundary of the given area, identified by its GeoNames id. Countries and administrative regions are valid areas; a city id is not.  Accepts exactly one id. A COMMA-SEPARATED LIST IS REJECTED with a 422 naming the limit — a deliberate departure from the comma-separated convention `country` uses, because each value would be a separate polygon intersection. Ask for one area per request.  COST: a request using this parameter consumes 2 quota units instead of 1, on every plan including Free. Combining it with `bbox` still costs 2, not 3 — the highest multiplier applies rather than the sum, and adding a box makes the query cheaper to serve, so it is never penalised.  This asks a GEOMETRIC question and can therefore return a different set of cities than `/v1/regions/{id}/cities`, which asks an administrative one. See that endpoint's description for when and why the two disagree.  Two failures are reported with distinct 400 codes so a typo is distinguishable from a coverage gap: `area_not_an_area` means the id does not name a country or region at all, and `area_no_boundary` means it does but no boundary polygon is available for it yet.
  bbox: '-122.6,37.6,-122.2,37.9', # String | Return only results inside the bounding box, given as four comma-separated numbers in the order `w,s,e,n` — west longitude, south latitude, east longitude, north latitude.  Longitudes must be within [-180, 180] and latitudes within [-90, 90].  A box where WEST IS GREATER THAN EAST wraps the antimeridian and is fully supported: `bbox=170,-20,-170,-10` is a box around Fiji, evaluated as the union of the two halves it spans. Latitude has no equivalent wrap-around meaning, so `s` greater than `n` is a validation error rather than a wrapped box.  Charged at the standard request cost of 1 unit. Adding it to a `within` query narrows the candidate set before the polygon test and does not raise the charge.
  cursor: 'eyJpZCI6MjV9', # String | Pagination cursor from a previous response
  limit: 25, # Integer | Number of results per page (1-100, default 25)
  fields: 'name,population,iso_code', # String | Comma-separated list of fields to include in the response
  sort: 'postal_code' # String | Sort field. Allowed: postal_code, country_code, place_name, id.
}

begin
  # List postal codes
  result = api_instance.list_postal_codes(opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling PostalCodesApi->list_postal_codes: #{e}"
end
```

#### Using the list_postal_codes_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<PostalCodeListResponse>, Integer, Hash)> list_postal_codes_with_http_info(opts)

```ruby
begin
  # List postal codes
  data, status_code, headers = api_instance.list_postal_codes_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <PostalCodeListResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling PostalCodesApi->list_postal_codes_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **country** | **String** | Filter by ISO alpha-2 country codes (comma-separated) | [optional] |
| **code** | **String** | Filter by postal code | [optional] |
| **within** | **Integer** | Return only results whose coordinates fall geometrically inside the boundary of the given area, identified by its GeoNames id. Countries and administrative regions are valid areas; a city id is not.  Accepts exactly one id. A COMMA-SEPARATED LIST IS REJECTED with a 422 naming the limit — a deliberate departure from the comma-separated convention &#x60;country&#x60; uses, because each value would be a separate polygon intersection. Ask for one area per request.  COST: a request using this parameter consumes 2 quota units instead of 1, on every plan including Free. Combining it with &#x60;bbox&#x60; still costs 2, not 3 — the highest multiplier applies rather than the sum, and adding a box makes the query cheaper to serve, so it is never penalised.  This asks a GEOMETRIC question and can therefore return a different set of cities than &#x60;/v1/regions/{id}/cities&#x60;, which asks an administrative one. See that endpoint&#39;s description for when and why the two disagree.  Two failures are reported with distinct 400 codes so a typo is distinguishable from a coverage gap: &#x60;area_not_an_area&#x60; means the id does not name a country or region at all, and &#x60;area_no_boundary&#x60; means it does but no boundary polygon is available for it yet. | [optional] |
| **bbox** | **String** | Return only results inside the bounding box, given as four comma-separated numbers in the order &#x60;w,s,e,n&#x60; — west longitude, south latitude, east longitude, north latitude.  Longitudes must be within [-180, 180] and latitudes within [-90, 90].  A box where WEST IS GREATER THAN EAST wraps the antimeridian and is fully supported: &#x60;bbox&#x3D;170,-20,-170,-10&#x60; is a box around Fiji, evaluated as the union of the two halves it spans. Latitude has no equivalent wrap-around meaning, so &#x60;s&#x60; greater than &#x60;n&#x60; is a validation error rather than a wrapped box.  Charged at the standard request cost of 1 unit. Adding it to a &#x60;within&#x60; query narrows the candidate set before the polygon test and does not raise the charge. | [optional] |
| **cursor** | **String** | Pagination cursor from a previous response | [optional] |
| **limit** | **Integer** | Number of results per page (1-100, default 25) | [optional][default to 25] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |
| **sort** | **String** | Sort field. Allowed: postal_code, country_code, place_name, id. | [optional] |

### Return type

[**PostalCodeListResponse**](PostalCodeListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## nearest_postal_code

> <PostalCodeListResponse> nearest_postal_code(lat, lon, opts)

Find nearest postal codes

Returns the nearest postal codes to a given latitude/longitude using PostGIS spatial index.

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

api_instance = GeoAPI::PostalCodesApi.new
lat = 37.7749 # Float | Latitude (-90 to 90)
lon = -122.4194 # Float | Longitude (-180 to 180)
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  limit: 3 # Integer | Number of results (1-10, default 1)
}

begin
  # Find nearest postal codes
  result = api_instance.nearest_postal_code(lat, lon, opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling PostalCodesApi->nearest_postal_code: #{e}"
end
```

#### Using the nearest_postal_code_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<PostalCodeListResponse>, Integer, Hash)> nearest_postal_code_with_http_info(lat, lon, opts)

```ruby
begin
  # Find nearest postal codes
  data, status_code, headers = api_instance.nearest_postal_code_with_http_info(lat, lon, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <PostalCodeListResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling PostalCodesApi->nearest_postal_code_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lat** | **Float** | Latitude (-90 to 90) |  |
| **lon** | **Float** | Longitude (-180 to 180) |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **limit** | **Integer** | Number of results (1-10, default 1) | [optional][default to 1] |

### Return type

[**PostalCodeListResponse**](PostalCodeListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

