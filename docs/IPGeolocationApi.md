# GeoAPI::IPGeolocationApi

All URIs are relative to *https://geosearch.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**lookup_ip**](IPGeolocationApi.md#lookup_ip) | **GET** /v1/ip/{address} | IP geolocation lookup |
| [**lookup_my_ip**](IPGeolocationApi.md#lookup_my_ip) | **GET** /v1/ip/me | Caller&#39;s IP geolocation |


## lookup_ip

> <IPSingleResponse> lookup_ip(address, opts)

IP geolocation lookup

Returns geolocation data for a given IPv4 or IPv6 address.

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

api_instance = GeoAPI::IPGeolocationApi.new
address = '8.8.8.8' # String | IPv4 or IPv6 address
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # IP geolocation lookup
  result = api_instance.lookup_ip(address, opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling IPGeolocationApi->lookup_ip: #{e}"
end
```

#### Using the lookup_ip_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IPSingleResponse>, Integer, Hash)> lookup_ip_with_http_info(address, opts)

```ruby
begin
  # IP geolocation lookup
  data, status_code, headers = api_instance.lookup_ip_with_http_info(address, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IPSingleResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling IPGeolocationApi->lookup_ip_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **address** | **String** | IPv4 or IPv6 address |  |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**IPSingleResponse**](IPSingleResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## lookup_my_ip

> <IPSingleResponse> lookup_my_ip(opts)

Caller's IP geolocation

Auto-detects the client's IP address (from X-Forwarded-For or RemoteAddr) and returns its geolocation data. 

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

api_instance = GeoAPI::IPGeolocationApi.new
opts = {
  lang: 'de', # String | ISO 639-1 language code for localized names (e.g., de, fr, ja)
  fields: 'name,population,iso_code' # String | Comma-separated list of fields to include in the response
}

begin
  # Caller's IP geolocation
  result = api_instance.lookup_my_ip(opts)
  p result
rescue GeoAPI::ApiError => e
  puts "Error when calling IPGeolocationApi->lookup_my_ip: #{e}"
end
```

#### Using the lookup_my_ip_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IPSingleResponse>, Integer, Hash)> lookup_my_ip_with_http_info(opts)

```ruby
begin
  # Caller's IP geolocation
  data, status_code, headers = api_instance.lookup_my_ip_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IPSingleResponse>
rescue GeoAPI::ApiError => e
  puts "Error when calling IPGeolocationApi->lookup_my_ip_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **lang** | **String** | ISO 639-1 language code for localized names (e.g., de, fr, ja) | [optional] |
| **fields** | **String** | Comma-separated list of fields to include in the response | [optional] |

### Return type

[**IPSingleResponse**](IPSingleResponse.md)

### Authorization

[apiKeyAuth](../README.md#apiKeyAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

