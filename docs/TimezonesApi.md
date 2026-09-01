# GeoAPI::TimezonesApi

All URIs are relative to *https://geosearch.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_timezone**](TimezonesApi.md#get_timezone) | **GET** /v1/timezones/{tzId} | Get timezone by IANA ID |
| [**list_timezones**](TimezonesApi.md#list_timezones) | **GET** /v1/timezones | List timezones |


## get_timezone

> <TimezoneSingleResponse> get_timezone(tz_id, opts)

Get timezone by IANA ID

Returns a single timezone by its IANA identifier. Note: IANA timezone IDs contain slashes (e.g., America/New_York), so the path uses a wildcard match. 

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

api_instance = GeoAPI::TimezonesApi.new
tz_id = 'America/New_York' # String | IANA timezone ID (e.g., America/New_York)
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Get timezone by IANA ID
  result = api_instance.get_timezone(tz_id, opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling TimezonesApi->get_timezone: #{e}"
end
```

#### Using the get_timezone_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<TimezoneSingleResponse>, Integer, Hash)> get_timezone_with_http_info(tz_id, opts)

```ruby
begin
  # Get timezone by IANA ID
  data, status_code, headers = api_instance.get_timezone_with_http_info(tz_id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <TimezoneSingleResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling TimezonesApi->get_timezone_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **tz_id** | **String** | IANA timezone ID (e.g., America/New_York) |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**TimezoneSingleResponse**](TimezoneSingleResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_timezones

> <TimezoneListResponse> list_timezones(opts)

List timezones

Returns a paginated list of timezones with optional filtering by country.

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

api_instance = GeoAPI::TimezonesApi.new
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  country: 'US', # String | Filter by ISO alpha-2 country code
  cursor: 'eyJpZCI6MjV9', # String | Pagination cursor from a previous response
  limit: 25, # Integer | Number of results per page (1-100, default 25)
  fields: 'name,population,iso_code', # String | Comma-separated list of fields to include in the response
  sort: 'gmt_offset' # String | Sort field. Allowed: timezone_id, gmt_offset, country_code.
}

begin
  # List timezones
  result = api_instance.list_timezones(opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling TimezonesApi->list_timezones: #{e}"
end
```

#### Using the list_timezones_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<TimezoneListResponse>, Integer, Hash)> list_timezones_with_http_info(opts)

```ruby
begin
  # List timezones
  data, status_code, headers = api_instance.list_timezones_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <TimezoneListResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling TimezonesApi->list_timezones_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **country** | **String** | Filter by ISO alpha-2 country code | [optional] |
| **cursor** | **String** | Pagination cursor from a previous response | [optional] |
| **limit** | **Integer** | Number of results per page (1-100, default 25) | [optional][default to 25] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |
| **sort** | **String** | Sort field. Allowed: timezone_id, gmt_offset, country_code. | [optional] |

### Return type

[**TimezoneListResponse**](TimezoneListResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

