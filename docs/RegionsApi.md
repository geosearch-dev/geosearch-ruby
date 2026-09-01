# GeoAPI::RegionsApi

All URIs are relative to *http://localhost*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_region**](RegionsApi.md#get_region) | **GET** /v1/regions/{id} | Get region by ID |
| [**list_region_cities**](RegionsApi.md#list_region_cities) | **GET** /v1/regions/{id}/cities | List cities in a region |
| [**list_regions**](RegionsApi.md#list_regions) | **GET** /v1/regions | List regions |
| [**region_children**](RegionsApi.md#region_children) | **GET** /v1/regions/{id}/children | List child cities of a region |


## get_region

> <RegionSingleResponse> get_region(id, opts)

Get region by ID

Returns a single region by its numeric ID.

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

api_instance = GeoAPI::RegionsApi.new
id = 5332921 # Integer | Region ID
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Get region by ID
  result = api_instance.get_region(id, opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling RegionsApi->get_region: #{e}"
end
```

#### Using the get_region_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<RegionSingleResponse>, Integer, Hash)> get_region_with_http_info(id, opts)

```ruby
begin
  # Get region by ID
  data, status_code, headers = api_instance.get_region_with_http_info(id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <RegionSingleResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling RegionsApi->get_region_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Region ID |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**RegionSingleResponse**](RegionSingleResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_region_cities

> <CityListResponse> list_region_cities(id, opts)

List cities in a region

Returns a paginated list of cities within a specific region.  THIS ENDPOINT AND `/v1/cities?within=` ANSWER DIFFERENT QUESTIONS AND WILL SOMETIMES RETURN DIFFERENT CITIES FOR THE SAME REGION. That is intended, not a bug. This endpoint answers the ADMINISTRATIVE question — which cities are assigned to this region by GeoNames' own admin codes — while `?within=` answers the GEOMETRIC one, which cities fall inside the region's polygon. The two disagree wherever an enclave, an exclave or a blank admin code puts a city's assignment at odds with its location.  Use this endpoint when you want the official assignment; use `/v1/cities?within=` when you want what is physically inside the boundary. This one is charged at the standard 1 unit; `?within=` costs 2.

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

api_instance = GeoAPI::RegionsApi.new
id = 5332921 # Integer | Region ID
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  cursor: 'eyJpZCI6MjV9', # String | Pagination cursor from a previous response
  limit: 25, # Integer | Number of results per page (1-100, default 25)
  fields: 'name,population,iso_code', # String | Comma-separated list of fields to include in the response
  sort: '-population' # String | Sort field. Allowed: name, population.
}

begin
  # List cities in a region
  result = api_instance.list_region_cities(id, opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling RegionsApi->list_region_cities: #{e}"
end
```

#### Using the list_region_cities_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CityListResponse>, Integer, Hash)> list_region_cities_with_http_info(id, opts)

```ruby
begin
  # List cities in a region
  data, status_code, headers = api_instance.list_region_cities_with_http_info(id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CityListResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling RegionsApi->list_region_cities_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Region ID |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **cursor** | **String** | Pagination cursor from a previous response | [optional] |
| **limit** | **Integer** | Number of results per page (1-100, default 25) | [optional][default to 25] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |
| **sort** | **String** | Sort field. Allowed: name, population. | [optional] |

### Return type

[**CityListResponse**](CityListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_regions

> <RegionListResponse> list_regions(opts)

List regions

Returns a paginated list of regions with optional filtering by country, level, and population.

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

api_instance = GeoAPI::RegionsApi.new
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  country: 'US', # String | Filter by ISO alpha-2 country code
  level: 1, # Integer | Filter by administrative level
  population_min: 1000000, # Integer | Minimum population filter
  population_max: 10000000, # Integer | Maximum population filter
  cursor: 'eyJpZCI6MjV9', # String | Pagination cursor from a previous response
  limit: 25, # Integer | Number of results per page (1-100, default 25)
  fields: 'name,population,iso_code', # String | Comma-separated list of fields to include in the response
  sort: '-population' # String | Sort field. Allowed: name, population.
}

begin
  # List regions
  result = api_instance.list_regions(opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling RegionsApi->list_regions: #{e}"
end
```

#### Using the list_regions_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<RegionListResponse>, Integer, Hash)> list_regions_with_http_info(opts)

```ruby
begin
  # List regions
  data, status_code, headers = api_instance.list_regions_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <RegionListResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling RegionsApi->list_regions_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **country** | **String** | Filter by ISO alpha-2 country code | [optional] |
| **level** | **Integer** | Filter by administrative level | [optional] |
| **population_min** | **Integer** | Minimum population filter | [optional] |
| **population_max** | **Integer** | Maximum population filter | [optional] |
| **cursor** | **String** | Pagination cursor from a previous response | [optional] |
| **limit** | **Integer** | Number of results per page (1-100, default 25) | [optional][default to 25] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |
| **sort** | **String** | Sort field. Allowed: name, population. | [optional] |

### Return type

[**RegionListResponse**](RegionListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## region_children

> <CityListResponse> region_children(id, opts)

List child cities of a region

Returns all cities that are direct children of the specified region in the administrative hierarchy.

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

api_instance = GeoAPI::RegionsApi.new
id = 5332921 # Integer | Region ID
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # List child cities of a region
  result = api_instance.region_children(id, opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling RegionsApi->region_children: #{e}"
end
```

#### Using the region_children_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CityListResponse>, Integer, Hash)> region_children_with_http_info(id, opts)

```ruby
begin
  # List child cities of a region
  data, status_code, headers = api_instance.region_children_with_http_info(id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CityListResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling RegionsApi->region_children_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **Integer** | Region ID |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**CityListResponse**](CityListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

