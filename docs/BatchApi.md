# GeoSearch::BatchApi

All URIs are relative to *https://geosearch.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**batch_cities**](BatchApi.md#batch_cities) | **POST** /v1/batch/cities | Batch lookup cities by IDs |
| [**batch_countries**](BatchApi.md#batch_countries) | **POST** /v1/batch/countries | Batch lookup countries by IDs |
| [**batch_regions**](BatchApi.md#batch_regions) | **POST** /v1/batch/regions | Batch lookup regions by IDs |


## batch_cities

> <CityListResponse> batch_cities(batch_request, opts)

Batch lookup cities by IDs

Returns multiple cities in a single request. Maximum 50 IDs per request.

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

api_instance = GeoSearch::BatchApi.new
batch_request = GeoSearch::BatchRequest.new({ids: [5391959,  5128581,  4887398]}) # BatchRequest | 
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Batch lookup cities by IDs
  result = api_instance.batch_cities(batch_request, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling BatchApi->batch_cities: #{e}"
end
```

#### Using the batch_cities_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CityListResponse>, Integer, Hash)> batch_cities_with_http_info(batch_request, opts)

```ruby
begin
  # Batch lookup cities by IDs
  data, status_code, headers = api_instance.batch_cities_with_http_info(batch_request, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CityListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling BatchApi->batch_cities_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **batch_request** | [**BatchRequest**](BatchRequest.md) |  |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**CityListResponse**](CityListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## batch_countries

> <CountryListResponse> batch_countries(batch_request, opts)

Batch lookup countries by IDs

Returns multiple countries in a single request. Maximum 50 IDs per request.

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

api_instance = GeoSearch::BatchApi.new
batch_request = GeoSearch::BatchRequest.new({ids: [5391959,  5128581,  4887398]}) # BatchRequest | 
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Batch lookup countries by IDs
  result = api_instance.batch_countries(batch_request, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling BatchApi->batch_countries: #{e}"
end
```

#### Using the batch_countries_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CountryListResponse>, Integer, Hash)> batch_countries_with_http_info(batch_request, opts)

```ruby
begin
  # Batch lookup countries by IDs
  data, status_code, headers = api_instance.batch_countries_with_http_info(batch_request, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CountryListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling BatchApi->batch_countries_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **batch_request** | [**BatchRequest**](BatchRequest.md) |  |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**CountryListResponse**](CountryListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## batch_regions

> <RegionListResponse> batch_regions(batch_request, opts)

Batch lookup regions by IDs

Returns multiple regions in a single request. Maximum 50 IDs per request.

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

api_instance = GeoSearch::BatchApi.new
batch_request = GeoSearch::BatchRequest.new({ids: [5391959,  5128581,  4887398]}) # BatchRequest | 
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Batch lookup regions by IDs
  result = api_instance.batch_regions(batch_request, opts)
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling BatchApi->batch_regions: #{e}"
end
```

#### Using the batch_regions_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<RegionListResponse>, Integer, Hash)> batch_regions_with_http_info(batch_request, opts)

```ruby
begin
  # Batch lookup regions by IDs
  data, status_code, headers = api_instance.batch_regions_with_http_info(batch_request, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <RegionListResponse>
rescue GeoSearch::ApiError => e
  puts "Error when calling BatchApi->batch_regions_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **batch_request** | [**BatchRequest**](BatchRequest.md) |  |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**RegionListResponse**](RegionListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

