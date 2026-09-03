# GeoSearch::CountriesApi

All URIs are relative to *https://geosearch.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**country_neighbors**](CountriesApi.md#country_neighbors) | **GET** /v1/countries/{code}/neighbors | List neighboring countries |
| [**get_country**](CountriesApi.md#get_country) | **GET** /v1/countries/{code} | Get country by ISO code |
| [**list_countries**](CountriesApi.md#list_countries) | **GET** /v1/countries | List countries |
| [**list_country_regions**](CountriesApi.md#list_country_regions) | **GET** /v1/countries/{code}/regions | List regions in a country |


## country_neighbors

> <CountryListResponse> country_neighbors(code, opts)

List neighboring countries

Returns countries that share a border with the specified country.

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

api_instance = GeoSearch::CountriesApi.new
code = 'DE' # String | ISO alpha-2 country code
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # List neighboring countries
  result = api_instance.country_neighbors(code, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling CountriesApi->country_neighbors: #{e}"
end
```

#### Using the country_neighbors_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CountryListResponse>, Integer, Hash)> country_neighbors_with_http_info(code, opts)

```ruby
begin
  # List neighboring countries
  data, status_code, headers = api_instance.country_neighbors_with_http_info(code, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CountryListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling CountriesApi->country_neighbors_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **code** | **String** | ISO alpha-2 country code |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**CountryListResponse**](CountryListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_country

> <CountrySingleResponse> get_country(code, opts)

Get country by ISO code

Returns a single country by its ISO alpha-2 code.

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

api_instance = GeoSearch::CountriesApi.new
code = 'US' # String | ISO alpha-2 country code
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Get country by ISO code
  result = api_instance.get_country(code, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling CountriesApi->get_country: #{e}"
end
```

#### Using the get_country_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CountrySingleResponse>, Integer, Hash)> get_country_with_http_info(code, opts)

```ruby
begin
  # Get country by ISO code
  data, status_code, headers = api_instance.get_country_with_http_info(code, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CountrySingleResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling CountriesApi->get_country_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **code** | **String** | ISO alpha-2 country code |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**CountrySingleResponse**](CountrySingleResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_countries

> <CountryListResponse> list_countries(opts)

List countries

Returns a paginated list of countries with optional filtering and sorting.

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

api_instance = GeoSearch::CountriesApi.new
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  continent: 'AF', # String | Filter by continent code (AF, AN, AS, EU, NA, OC, SA)
  iso_code: 'US,CA,GB', # String | Filter by ISO alpha-2 codes (comma-separated)
  population_min: 1000000, # Integer | Minimum population filter
  population_max: 10000000, # Integer | Maximum population filter
  cursor: 'eyJpZCI6MjV9', # String | Pagination cursor from a previous response
  limit: 25, # Integer | Number of results per page (1-100, default 25)
  fields: 'name,population,iso_code', # String | Comma-separated list of fields to include in the response
  sort: '-population' # String | Sort field and direction. Allowed: name, population, area_sq_km. Prefix with - for descending.
}

begin
  # List countries
  result = api_instance.list_countries(opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling CountriesApi->list_countries: #{e}"
end
```

#### Using the list_countries_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CountryListResponse>, Integer, Hash)> list_countries_with_http_info(opts)

```ruby
begin
  # List countries
  data, status_code, headers = api_instance.list_countries_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CountryListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling CountriesApi->list_countries_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **continent** | **String** | Filter by continent code (AF, AN, AS, EU, NA, OC, SA) | [optional] |
| **iso_code** | **String** | Filter by ISO alpha-2 codes (comma-separated) | [optional] |
| **population_min** | **Integer** | Minimum population filter | [optional] |
| **population_max** | **Integer** | Maximum population filter | [optional] |
| **cursor** | **String** | Pagination cursor from a previous response | [optional] |
| **limit** | **Integer** | Number of results per page (1-100, default 25) | [optional][default to 25] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |
| **sort** | **String** | Sort field and direction. Allowed: name, population, area_sq_km. Prefix with - for descending. | [optional] |

### Return type

[**CountryListResponse**](CountryListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_country_regions

> <RegionListResponse> list_country_regions(code, opts)

List regions in a country

Returns a paginated list of regions (administrative divisions) within a country.

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

api_instance = GeoSearch::CountriesApi.new
code = 'US' # String | ISO alpha-2 country code
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  cursor: 'eyJpZCI6MjV9', # String | Pagination cursor from a previous response
  limit: 25, # Integer | Number of results per page (1-100, default 25)
  fields: 'name,population,iso_code', # String | Comma-separated list of fields to include in the response
  sort: 'name' # String | Sort field. Allowed: name, population.
}

begin
  # List regions in a country
  result = api_instance.list_country_regions(code, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling CountriesApi->list_country_regions: #{e}"
end
```

#### Using the list_country_regions_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<RegionListResponse>, Integer, Hash)> list_country_regions_with_http_info(code, opts)

```ruby
begin
  # List regions in a country
  data, status_code, headers = api_instance.list_country_regions_with_http_info(code, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <RegionListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling CountriesApi->list_country_regions_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **code** | **String** | ISO alpha-2 country code |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
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

