# GeoSearch::CitiesApi

All URIs are relative to *https://geosearch.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**city_hierarchy**](CitiesApi.md#city_hierarchy) | **GET** /v1/cities/{id}/hierarchy | Get administrative hierarchy for a city |
| [**get_city**](CitiesApi.md#get_city) | **GET** /v1/cities/{id} | Get city by ID |
| [**list_cities**](CitiesApi.md#list_cities) | **GET** /v1/cities | List cities |
| [**nearby_cities**](CitiesApi.md#nearby_cities) | **GET** /v1/cities/nearby | Find nearby cities |


## city_hierarchy

> <HierarchyListResponse> city_hierarchy(id, opts)

Get administrative hierarchy for a city

Returns the full administrative hierarchy for a city, ordered from the city itself up through region, country, and continent. 

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

api_instance = GeoSearch::CitiesApi.new
id = 5391959 # Integer | City ID
opts = {
  lang: 'de' # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
}

begin
  # Get administrative hierarchy for a city
  result = api_instance.city_hierarchy(id, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling CitiesApi->city_hierarchy: #{e}"
end
```

#### Using the city_hierarchy_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<HierarchyListResponse>, Integer, Hash)> city_hierarchy_with_http_info(id, opts)

```ruby
begin
  # Get administrative hierarchy for a city
  data, status_code, headers = api_instance.city_hierarchy_with_http_info(id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <HierarchyListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling CitiesApi->city_hierarchy_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | City ID |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |

### Return type

[**HierarchyListResponse**](HierarchyListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_city

> <CitySingleResponse> get_city(id, opts)

Get city by ID

Returns a single city by its numeric ID.

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

api_instance = GeoSearch::CitiesApi.new
id = 5391959 # Integer | City ID
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Get city by ID
  result = api_instance.get_city(id, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling CitiesApi->get_city: #{e}"
end
```

#### Using the get_city_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CitySingleResponse>, Integer, Hash)> get_city_with_http_info(id, opts)

```ruby
begin
  # Get city by ID
  data, status_code, headers = api_instance.get_city_with_http_info(id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CitySingleResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling CitiesApi->get_city_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | City ID |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**CitySingleResponse**](CitySingleResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_cities

> <CityListResponse> list_cities(opts)

List cities

Returns a paginated list of cities with optional filtering by country, admin code, name, population, timezone, and elevation.

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

api_instance = GeoSearch::CitiesApi.new
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  country: 'US,CA', # String | Filter by ISO alpha-2 country codes (comma-separated)
  admin1: 'CA', # String | Filter by admin1 code (state/province)
  name: 'San Fran', # String | Filter by city name (trigram fuzzy search)
  population_min: 1000000, # Integer | Minimum population filter
  population_max: 10000000, # Integer | Maximum population filter
  timezone: 'America/Los_Angeles', # String | Filter by IANA timezone ID
  min_elevation: 500, # Integer | Minimum elevation in meters
  max_elevation: 3000, # Integer | Maximum elevation in meters
  within: 6252001, # Integer | Return only results whose coordinates fall geometrically inside the boundary of the given area, identified by its GeoNames id. Countries and administrative regions are valid areas; a city id is not.  Accepts exactly one id. A COMMA-SEPARATED LIST IS REJECTED with a 422 naming the limit — a deliberate departure from the comma-separated convention `country` uses, because each value would be a separate polygon intersection. Ask for one area per request.  COST: a request using this parameter consumes 2 quota units instead of 1, on every plan including Free. Combining it with `bbox` still costs 2, not 3 — the highest multiplier applies rather than the sum, and adding a box makes the query cheaper to serve, so it is never penalised.  This asks a GEOMETRIC question and can therefore return a different set of cities than `/v1/regions/{id}/cities`, which asks an administrative one. See that endpoint's description for when and why the two disagree.  Two failures are reported with distinct 400 codes so a typo is distinguishable from a coverage gap: `area_not_an_area` means the id does not name a country or region at all, and `area_no_boundary` means it does but no boundary polygon is available for it yet.
  bbox: '-122.6,37.6,-122.2,37.9', # String | Return only results inside the bounding box, given as four comma-separated numbers in the order `w,s,e,n` — west longitude, south latitude, east longitude, north latitude.  Longitudes must be within [-180, 180] and latitudes within [-90, 90].  A box where WEST IS GREATER THAN EAST wraps the antimeridian and is fully supported: `bbox=170,-20,-170,-10` is a box around Fiji, evaluated as the union of the two halves it spans. Latitude has no equivalent wrap-around meaning, so `s` greater than `n` is a validation error rather than a wrapped box.  Charged at the standard request cost of 1 unit. Adding it to a `within` query narrows the candidate set before the polygon test and does not raise the charge.
  cursor: 'eyJpZCI6MjV9', # String | Pagination cursor from a previous response
  limit: 25, # Integer | Number of results per page (1-100, default 25)
  fields: 'name,population,iso_code', # String | Comma-separated list of fields to include in the response
  sort: '-population' # String | Sort field. Allowed: name, population, elevation, id.
}

begin
  # List cities
  result = api_instance.list_cities(opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling CitiesApi->list_cities: #{e}"
end
```

#### Using the list_cities_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CityListResponse>, Integer, Hash)> list_cities_with_http_info(opts)

```ruby
begin
  # List cities
  data, status_code, headers = api_instance.list_cities_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CityListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling CitiesApi->list_cities_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **country** | **String** | Filter by ISO alpha-2 country codes (comma-separated) | [optional] |
| **admin1** | **String** | Filter by admin1 code (state/province) | [optional] |
| **name** | **String** | Filter by city name (trigram fuzzy search) | [optional] |
| **population_min** | **Integer** | Minimum population filter | [optional] |
| **population_max** | **Integer** | Maximum population filter | [optional] |
| **timezone** | **String** | Filter by IANA timezone ID | [optional] |
| **min_elevation** | **Integer** | Minimum elevation in meters | [optional] |
| **max_elevation** | **Integer** | Maximum elevation in meters | [optional] |
| **within** | **Integer** | Return only results whose coordinates fall geometrically inside the boundary of the given area, identified by its GeoNames id. Countries and administrative regions are valid areas; a city id is not.  Accepts exactly one id. A COMMA-SEPARATED LIST IS REJECTED with a 422 naming the limit — a deliberate departure from the comma-separated convention &#x60;country&#x60; uses, because each value would be a separate polygon intersection. Ask for one area per request.  COST: a request using this parameter consumes 2 quota units instead of 1, on every plan including Free. Combining it with &#x60;bbox&#x60; still costs 2, not 3 — the highest multiplier applies rather than the sum, and adding a box makes the query cheaper to serve, so it is never penalised.  This asks a GEOMETRIC question and can therefore return a different set of cities than &#x60;/v1/regions/{id}/cities&#x60;, which asks an administrative one. See that endpoint&#39;s description for when and why the two disagree.  Two failures are reported with distinct 400 codes so a typo is distinguishable from a coverage gap: &#x60;area_not_an_area&#x60; means the id does not name a country or region at all, and &#x60;area_no_boundary&#x60; means it does but no boundary polygon is available for it yet. | [optional] |
| **bbox** | **String** | Return only results inside the bounding box, given as four comma-separated numbers in the order &#x60;w,s,e,n&#x60; — west longitude, south latitude, east longitude, north latitude.  Longitudes must be within [-180, 180] and latitudes within [-90, 90].  A box where WEST IS GREATER THAN EAST wraps the antimeridian and is fully supported: &#x60;bbox&#x3D;170,-20,-170,-10&#x60; is a box around Fiji, evaluated as the union of the two halves it spans. Latitude has no equivalent wrap-around meaning, so &#x60;s&#x60; greater than &#x60;n&#x60; is a validation error rather than a wrapped box.  Charged at the standard request cost of 1 unit. Adding it to a &#x60;within&#x60; query narrows the candidate set before the polygon test and does not raise the charge. | [optional] |
| **cursor** | **String** | Pagination cursor from a previous response | [optional] |
| **limit** | **Integer** | Number of results per page (1-100, default 25) | [optional][default to 25] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |
| **sort** | **String** | Sort field. Allowed: name, population, elevation, id. | [optional] |

### Return type

[**CityListResponse**](CityListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## nearby_cities

> <NearbyCityListResponse> nearby_cities(lat, lon, opts)

Find nearby cities

Returns cities near a given latitude/longitude within a specified radius. Results are ordered by distance. Uses PostGIS spatial index for fast lookups. 

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

api_instance = GeoSearch::CitiesApi.new
lat = 37.7749 # Float | Latitude (-90 to 90)
lon = -122.4194 # Float | Longitude (-180 to 180)
opts = {
  radius: 50, # Float | Search radius in kilometers (default 50, max 200)
  limit: 10, # Integer | Maximum results to return (1-250, default 10)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Find nearby cities
  result = api_instance.nearby_cities(lat, lon, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling CitiesApi->nearby_cities: #{e}"
end
```

#### Using the nearby_cities_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<NearbyCityListResponse>, Integer, Hash)> nearby_cities_with_http_info(lat, lon, opts)

```ruby
begin
  # Find nearby cities
  data, status_code, headers = api_instance.nearby_cities_with_http_info(lat, lon, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <NearbyCityListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling CitiesApi->nearby_cities_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lat** | **Float** | Latitude (-90 to 90) |  |
| **lon** | **Float** | Longitude (-180 to 180) |  |
| **radius** | **Float** | Search radius in kilometers (default 50, max 200) | [optional][default to 50] |
| **limit** | **Integer** | Maximum results to return (1-250, default 10) | [optional][default to 10] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**NearbyCityListResponse**](NearbyCityListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

