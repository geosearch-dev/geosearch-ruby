# GeoSearch::SearchApi

All URIs are relative to *https://geosearch.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**autocomplete**](SearchApi.md#autocomplete) | **GET** /v1/autocomplete | Autocomplete search |
| [**resolve_coordinate**](SearchApi.md#resolve_coordinate) | **GET** /v1/resolve | Resolve coordinates to their containing administrative areas |
| [**reverse_geocode**](SearchApi.md#reverse_geocode) | **GET** /v1/reverse | Reverse geocode coordinates |
| [**search**](SearchApi.md#search) | **GET** /v1/search | Cross-type search |


## autocomplete

> <AutocompleteListResponse> autocomplete(q, opts)

Autocomplete search

Returns autocomplete suggestions matching a query string across cities, regions, and countries. Results are ranked by relevance and population. Minimum 2 characters required. 

### Examples

```ruby
require 'time'
require 'geosearch'
# setup authorization
GeoSearch.configure do |config|
  # Configure API key authorization: apiKeyAuth
  config.api_key['X-API-Key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-API-Key'] = 'Bearer'
end

api_instance = GeoSearch::SearchApi.new
q = 'San Fran' # String | Search query (minimum 2 characters)
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  limit: 10, # Integer | Maximum results to return (1-25, default 10)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Autocomplete search
  result = api_instance.autocomplete(q, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling SearchApi->autocomplete: #{e}"
end
```

#### Using the autocomplete_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<AutocompleteListResponse>, Integer, Hash)> autocomplete_with_http_info(q, opts)

```ruby
begin
  # Autocomplete search
  data, status_code, headers = api_instance.autocomplete_with_http_info(q, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <AutocompleteListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling SearchApi->autocomplete_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **q** | **String** | Search query (minimum 2 characters) |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **limit** | **Integer** | Maximum results to return (1-25, default 10) | [optional][default to 10] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**AutocompleteListResponse**](AutocompleteListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## resolve_coordinate

> <HierarchyListResponse> resolve_coordinate(lat, lon, opts)

Resolve coordinates to their containing administrative areas

Returns the administrative areas whose BOUNDARY POLYGONS CONTAIN the given coordinate, ordered country first.  ## How this differs from `/v1/reverse`  These two endpoints take the same parameters and answer different questions, and the difference is the reason both exist.  `/v1/reverse` returns the NEAREST city. It always returns something, and for a point near a border that something is sometimes in the neighbouring country.  `/v1/resolve` returns the areas that actually CONTAIN the point. It is never wrong about which country a point is in — and it sometimes returns nothing at all, because no polygon covers the point or because we hold no polygon for that country. Choose this endpoint when correctness at borders matters and choose `/v1/reverse` when you always need an answer.  ## `depth` RUNS THE OPPOSITE DIRECTION FROM `/v1/cities/{id}/hierarchy`  Read this before writing code that consumes both endpoints.  Both return the same node SHAPE — `geoname_id`, `name`, `type`, `depth` — so one rendering path can accept either. The `depth` SEMANTICS are inverted between them:  - On **this** endpoint `depth` is POSITIONAL, counting outward-in from   the largest area: **`depth: 0` is the COUNTRY**, `depth: 1` is the   region inside it, and so on. - On **`/v1/cities/{id}/hierarchy`** `depth` counts up from the entity   that was asked about: `depth: 0` is the CITY, and the country is at the   highest depth in the list.  So `data[0]` is the country here and the city there. Code that sorts or indexes on `depth` across both endpoints without accounting for this will silently invert the hierarchy rather than fail.  ## Cost and availability  One quota unit, on every plan including Free. This is a single indexed point-in-polygon probe returning names, not a geometry transfer, so it carries no premium and no tier gate.  `?fields=` IS NOT SUPPORTED on this endpoint and is ignored if sent. The four node fields are all small, so selection would save nothing. 

### Examples

```ruby
require 'time'
require 'geosearch'
# setup authorization
GeoSearch.configure do |config|
  # Configure API key authorization: apiKeyAuth
  config.api_key['X-API-Key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-API-Key'] = 'Bearer'
end

api_instance = GeoSearch::SearchApi.new
lat = 37.7749 # Float | Latitude (-90 to 90). Must be a finite number: `NaN` and `Infinity` are rejected with a 400 rather than being passed to the spatial index, which would answer them with an ordinary \"not found\".
lon = -122.4194 # Float | Longitude (-180 to 180). Must be a finite number; see `lat`.
opts = {
  lang: 'de' # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
}

begin
  # Resolve coordinates to their containing administrative areas
  result = api_instance.resolve_coordinate(lat, lon, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling SearchApi->resolve_coordinate: #{e}"
end
```

#### Using the resolve_coordinate_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<HierarchyListResponse>, Integer, Hash)> resolve_coordinate_with_http_info(lat, lon, opts)

```ruby
begin
  # Resolve coordinates to their containing administrative areas
  data, status_code, headers = api_instance.resolve_coordinate_with_http_info(lat, lon, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <HierarchyListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling SearchApi->resolve_coordinate_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lat** | **Float** | Latitude (-90 to 90). Must be a finite number: &#x60;NaN&#x60; and &#x60;Infinity&#x60; are rejected with a 400 rather than being passed to the spatial index, which would answer them with an ordinary \&quot;not found\&quot;. |  |
| **lon** | **Float** | Longitude (-180 to 180). Must be a finite number; see &#x60;lat&#x60;. |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |

### Return type

[**HierarchyListResponse**](HierarchyListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## reverse_geocode

> <ReverseGeocodeSingleResponse> reverse_geocode(lat, lon, opts)

Reverse geocode coordinates

Returns the nearest city for a given latitude/longitude. Uses PostGIS spatial index for fast reverse geocoding. 

### Examples

```ruby
require 'time'
require 'geosearch'
# setup authorization
GeoSearch.configure do |config|
  # Configure API key authorization: apiKeyAuth
  config.api_key['X-API-Key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-API-Key'] = 'Bearer'
end

api_instance = GeoSearch::SearchApi.new
lat = 37.7749 # Float | Latitude (-90 to 90)
lon = -122.4194 # Float | Longitude (-180 to 180)
opts = {
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Reverse geocode coordinates
  result = api_instance.reverse_geocode(lat, lon, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling SearchApi->reverse_geocode: #{e}"
end
```

#### Using the reverse_geocode_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<ReverseGeocodeSingleResponse>, Integer, Hash)> reverse_geocode_with_http_info(lat, lon, opts)

```ruby
begin
  # Reverse geocode coordinates
  data, status_code, headers = api_instance.reverse_geocode_with_http_info(lat, lon, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <ReverseGeocodeSingleResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling SearchApi->reverse_geocode_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lat** | **Float** | Latitude (-90 to 90) |  |
| **lon** | **Float** | Longitude (-180 to 180) |  |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**ReverseGeocodeSingleResponse**](ReverseGeocodeSingleResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## search

> <SearchListResponse> search(q, opts)

Cross-type search

Performs a fuzzy text search across countries, regions, and cities using trigram matching. Results are ranked by relevance and population. Uses simple limit pagination (no cursor). 

### Examples

```ruby
require 'time'
require 'geosearch'
# setup authorization
GeoSearch.configure do |config|
  # Configure API key authorization: apiKeyAuth
  config.api_key['X-API-Key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['X-API-Key'] = 'Bearer'
end

api_instance = GeoSearch::SearchApi.new
q = 'San Fran' # String | Search query (minimum 2 characters)
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  type: 'city', # String | Filter by entity type (comma-separated). Allowed: country, region, city.
  limit: 10, # Integer | Maximum results to return (1-100, default 25)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Cross-type search
  result = api_instance.search(q, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling SearchApi->search: #{e}"
end
```

#### Using the search_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SearchListResponse>, Integer, Hash)> search_with_http_info(q, opts)

```ruby
begin
  # Cross-type search
  data, status_code, headers = api_instance.search_with_http_info(q, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <SearchListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling SearchApi->search_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **q** | **String** | Search query (minimum 2 characters) |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **type** | **String** | Filter by entity type (comma-separated). Allowed: country, region, city. | [optional] |
| **limit** | **Integer** | Maximum results to return (1-100, default 25) | [optional][default to 25] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**SearchListResponse**](SearchListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

