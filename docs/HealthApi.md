# GeoSearch::HealthApi

All URIs are relative to *https://geosearch.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**get_status**](HealthApi.md#get_status) | **GET** /v1/status | Health check |


## get_status

> <GetStatus200Response> get_status

Health check

Returns the API health status and database connectivity. No authentication required.

### Examples

```ruby
require 'time'
require 'geosearch'

api_instance = GeoSearch::HealthApi.new

begin
  # Health check
  result = api_instance.get_status
  p result
rescue GeoSearch::ApiError => e
  puts "Error when calling HealthApi->get_status: #{e}"
end
```

#### Using the get_status_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<GetStatus200Response>, Integer, Hash)> get_status_with_http_info

```ruby
begin
  # Health check
  data, status_code, headers = api_instance.get_status_with_http_info
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <GetStatus200Response>
rescue GeoSearch::ApiError => e
  puts "Error when calling HealthApi->get_status_with_http_info: #{e}"
end
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**GetStatus200Response**](GetStatus200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

