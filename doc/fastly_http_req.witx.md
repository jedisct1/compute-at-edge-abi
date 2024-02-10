
# Module: fastly_http_req

## Table of contents

### Types list:

[**[All](#types)**] - [_[`fastly_status`](#fastly_status)_] - [_[`http_version`](#http_version)_] - [_[`http_status`](#http_status)_] - [_[`body_write_end`](#body_write_end)_] - [_[`body_handle`](#body_handle)_] - [_[`request_handle`](#request_handle)_] - [_[`response_handle`](#response_handle)_] - [_[`pending_request_handle`](#pending_request_handle)_] - [_[`endpoint_handle`](#endpoint_handle)_] - [_[`dictionary_handle`](#dictionary_handle)_] - [_[`object_store_handle`](#object_store_handle)_] - [_[`pending_object_store_lookup_handle`](#pending_object_store_lookup_handle)_] - [_[`pending_object_store_insert_handle`](#pending_object_store_insert_handle)_] - [_[`pending_object_store_delete_handle`](#pending_object_store_delete_handle)_] - [_[`secret_store_handle`](#secret_store_handle)_] - [_[`secret_handle`](#secret_handle)_] - [_[`async_item_handle`](#async_item_handle)_] - [_[`multi_value_cursor`](#multi_value_cursor)_] - [_[`multi_value_cursor_result`](#multi_value_cursor_result)_] - [_[`cache_override_tag`](#cache_override_tag)_] - [_[`num_bytes`](#num_bytes)_] - [_[`header_count`](#header_count)_] - [_[`is_done`](#is_done)_] - [_[`done_idx`](#done_idx)_] - [_[`is_valid`](#is_valid)_] - [_[`inserted`](#inserted)_] - [_[`ready_idx`](#ready_idx)_] - [_[`port`](#port)_] - [_[`timeout_ms`](#timeout_ms)_] - [_[`backend_exists`](#backend_exists)_] - [_[`is_dynamic`](#is_dynamic)_] - [_[`is_ssl`](#is_ssl)_] - [_[`backend_health`](#backend_health)_] - [_[`content_encodings`](#content_encodings)_] - [_[`framing_headers_mode`](#framing_headers_mode)_] - [_[`http_keepalive_mode`](#http_keepalive_mode)_] - [_[`tls_version`](#tls_version)_] - [_[`backend_config_options`](#backend_config_options)_] - [_[`dynamic_backend_config`](#dynamic_backend_config)_] - [_[`client_cert_verify_result`](#client_cert_verify_result)_] - [_[`purge_options_mask`](#purge_options_mask)_] - [_[`purge_options`](#purge_options)_] - [_[`send_error_detail_tag`](#send_error_detail_tag)_] - [_[`send_error_detail_mask`](#send_error_detail_mask)_] - [_[`send_error_detail`](#send_error_detail)_] - [_[`blocked`](#blocked)_] - [_[`rate`](#rate)_] - [_[`count`](#count)_] - [_[`has`](#has)_] - [_[`body_length`](#body_length)_]

### Functions list:

[**[All](#functions)**] - [[`body_downstream_get()`](#body_downstream_get)] - [[`cache_override_set()`](#cache_override_set)] - [[`cache_override_v2_set()`](#cache_override_v2_set)] - [[`downstream_client_ip_addr()`](#downstream_client_ip_addr)] - [[`downstream_client_h2_fingerprint()`](#downstream_client_h2_fingerprint)] - [[`downstream_client_request_id()`](#downstream_client_request_id)] - [[`downstream_client_oh_fingerprint()`](#downstream_client_oh_fingerprint)] - [[`downstream_tls_cipher_openssl_name()`](#downstream_tls_cipher_openssl_name)] - [[`downstream_tls_protocol()`](#downstream_tls_protocol)] - [[`downstream_tls_client_hello()`](#downstream_tls_client_hello)] - [[`downstream_tls_raw_client_certificate()`](#downstream_tls_raw_client_certificate)] - [[`downstream_tls_client_cert_verify_result()`](#downstream_tls_client_cert_verify_result)] - [[`downstream_tls_ja3_md5()`](#downstream_tls_ja3_md5)] - [[`downstream_tls_ja4()`](#downstream_tls_ja4)] - [[`new()`](#new)] - [[`header_names_get()`](#header_names_get)] - [[`original_header_names_get()`](#original_header_names_get)] - [[`original_header_count()`](#original_header_count)] - [[`header_value_get()`](#header_value_get)] - [[`header_values_get()`](#header_values_get)] - [[`header_values_set()`](#header_values_set)] - [[`header_insert()`](#header_insert)] - [[`header_append()`](#header_append)] - [[`header_remove()`](#header_remove)] - [[`method_get()`](#method_get)] - [[`method_set()`](#method_set)] - [[`uri_get()`](#uri_get)] - [[`uri_set()`](#uri_set)] - [[`version_get()`](#version_get)] - [[`version_set()`](#version_set)] - [[`send()`](#send)] - [[`send_v2()`](#send_v2)] - [[`send_async()`](#send_async)] - [[`send_async_streaming()`](#send_async_streaming)] - [[`pending_req_poll()`](#pending_req_poll)] - [[`pending_req_poll_v2()`](#pending_req_poll_v2)] - [[`pending_req_wait()`](#pending_req_wait)] - [[`pending_req_wait_v2()`](#pending_req_wait_v2)] - [[`pending_req_select()`](#pending_req_select)] - [[`pending_req_select_v2()`](#pending_req_select_v2)] - [[`fastly_key_is_valid()`](#fastly_key_is_valid)] - [[`close()`](#close)] - [[`auto_decompress_response_set()`](#auto_decompress_response_set)] - [[`upgrade_websocket()`](#upgrade_websocket)] - [[`redirect_to_websocket_proxy()`](#redirect_to_websocket_proxy)] - [[`redirect_to_grip_proxy()`](#redirect_to_grip_proxy)] - [[`redirect_to_websocket_proxy_v2()`](#redirect_to_websocket_proxy_v2)] - [[`redirect_to_grip_proxy_v2()`](#redirect_to_grip_proxy_v2)] - [[`framing_headers_mode_set()`](#framing_headers_mode_set)] - [[`register_dynamic_backend()`](#register_dynamic_backend)]

## Types

### _[`fastly_status`](#fastly_status)_

Enumeration with tag type: `u32`, and the following members:

* **`ok`**: _[`fastly_status`](#fastly_status)_
* **`error`**: _[`fastly_status`](#fastly_status)_
* **`inval`**: _[`fastly_status`](#fastly_status)_
* **`badf`**: _[`fastly_status`](#fastly_status)_
* **`buflen`**: _[`fastly_status`](#fastly_status)_
* **`unsupported`**: _[`fastly_status`](#fastly_status)_
* **`badalign`**: _[`fastly_status`](#fastly_status)_
* **`httpinvalid`**: _[`fastly_status`](#fastly_status)_
* **`httpuser`**: _[`fastly_status`](#fastly_status)_
* **`httpincomplete`**: _[`fastly_status`](#fastly_status)_
* **`none`**: _[`fastly_status`](#fastly_status)_
* **`httpheadtoolarge`**: _[`fastly_status`](#fastly_status)_
* **`httpinvalidstatus`**: _[`fastly_status`](#fastly_status)_
* **`limitexceeded`**: _[`fastly_status`](#fastly_status)_
* **`again`**: _[`fastly_status`](#fastly_status)_

> Status codes returned from hostcalls.


---

### _[`http_version`](#http_version)_

Enumeration with tag type: `u32`, and the following members:

* **`http_09`**: _[`http_version`](#http_version)_
* **`http_10`**: _[`http_version`](#http_version)_
* **`http_11`**: _[`http_version`](#http_version)_
* **`h2`**: _[`http_version`](#http_version)_
* **`h3`**: _[`http_version`](#http_version)_

> A tag indicating HTTP protocol versions.


---

### _[`http_status`](#http_status)_
Alias for `u16`.


> HTTP status codes.


---

### _[`body_write_end`](#body_write_end)_

Enumeration with tag type: `u32`, and the following members:

* **`back`**: _[`body_write_end`](#body_write_end)_
* **`front`**: _[`body_write_end`](#body_write_end)_

---

### _[`body_handle`](#body_handle)_
Alias for `handle`.


> A handle to an HTTP request or response body.


---

### _[`request_handle`](#request_handle)_
Alias for `handle`.


> A handle to an HTTP request.


---

### _[`response_handle`](#response_handle)_
Alias for `handle`.


> A handle to an HTTP response.


---

### _[`pending_request_handle`](#pending_request_handle)_
Alias for `handle`.


> A handle to a currently-pending asynchronous HTTP request.


---

### _[`endpoint_handle`](#endpoint_handle)_
Alias for `handle`.


> A handle to a logging endpoint.


---

### _[`dictionary_handle`](#dictionary_handle)_
Alias for `handle`.


> A handle to an Edge Dictionary.


---

### _[`object_store_handle`](#object_store_handle)_
Alias for `handle`.


> A handle to an Object Store.


---

### _[`pending_object_store_lookup_handle`](#pending_object_store_lookup_handle)_
Alias for `handle`.


> A handle to a pending Object Store lookup.


---

### _[`pending_object_store_insert_handle`](#pending_object_store_insert_handle)_
Alias for `handle`.


> A handle to a pending Object Store insert.


---

### _[`pending_object_store_delete_handle`](#pending_object_store_delete_handle)_
Alias for `handle`.


> A handle to a pending Object Store delete.


---

### _[`secret_store_handle`](#secret_store_handle)_
Alias for `handle`.


> A handle to a Secret Store.


---

### _[`secret_handle`](#secret_handle)_
Alias for `handle`.


> A handle to an individual secret.


---

### _[`async_item_handle`](#async_item_handle)_
Alias for `handle`.


> A handle to an object supporting generic async operations.
> Can be either a `body_handle` or a `pending_request_handle`.
>
> Each async item has an associated I/O action:
>
> * Pending requests: awaiting the response headers / `Response` object
> * Normal bodies: reading bytes from the body
> * Streaming bodies: writing bytes to the body
>
> For writing bytes, note that there is a large host-side buffer that bytes can eagerly be written
> into, even before the origin itself consumes that data.


---

### _[`multi_value_cursor`](#multi_value_cursor)_
Alias for `u32`.


> A "multi-value" cursor.


---

### _[`multi_value_cursor_result`](#multi_value_cursor_result)_
Alias for `i64`.


> -1 represents "finished", non-negative represents a $multi_value_cursor:


---

### _[`cache_override_tag`](#cache_override_tag)_

Set of constants, of type `u32`

Predefined constants for _[`cache_override_tag`](#cache_override_tag)_:

* **`pass`** = `0x1`
* **`ttl`** = `0x2`
* **`stale_while_revalidate`** = `0x4`
* **`pci`** = `0x8`

> An override for response caching behavior.
> A zero value indicates that the origin response's cache control headers should be used.


---

### _[`num_bytes`](#num_bytes)_
Alias for `usize`.


---

### _[`header_count`](#header_count)_
Alias for `u32`.


---

### _[`is_done`](#is_done)_
Alias for `u32`.


---

### _[`done_idx`](#done_idx)_
Alias for `u32`.


---

### _[`is_valid`](#is_valid)_
Alias for `u32`.


---

### _[`inserted`](#inserted)_
Alias for `u32`.


---

### _[`ready_idx`](#ready_idx)_
Alias for `u32`.


---

### _[`port`](#port)_
Alias for `u16`.


---

### _[`timeout_ms`](#timeout_ms)_
Alias for `u32`.


---

### _[`backend_exists`](#backend_exists)_
Alias for `u32`.


---

### _[`is_dynamic`](#is_dynamic)_
Alias for `u32`.


---

### _[`is_ssl`](#is_ssl)_
Alias for `u32`.


---

### _[`backend_health`](#backend_health)_

Enumeration with tag type: `u32`, and the following members:

* **`unknown`**: _[`backend_health`](#backend_health)_
* **`healthy`**: _[`backend_health`](#backend_health)_
* **`unhealthy`**: _[`backend_health`](#backend_health)_

---

### _[`content_encodings`](#content_encodings)_

Set of constants, of type `u32`

Predefined constants for _[`content_encodings`](#content_encodings)_:

* **`gzip`** = `1`

---

### _[`framing_headers_mode`](#framing_headers_mode)_

Enumeration with tag type: `u32`, and the following members:

* **`automatic`**: _[`framing_headers_mode`](#framing_headers_mode)_
* **`manually_from_headers`**: _[`framing_headers_mode`](#framing_headers_mode)_

---

### _[`http_keepalive_mode`](#http_keepalive_mode)_

Enumeration with tag type: `u32`, and the following members:

* **`automatic`**: _[`http_keepalive_mode`](#http_keepalive_mode)_
* **`no_keepalive`**: _[`http_keepalive_mode`](#http_keepalive_mode)_

---

### _[`tls_version`](#tls_version)_

Enumeration with tag type: `u32`, and the following members:

* **`tls_1`**: _[`tls_version`](#tls_version)_
* **`tls_1_1`**: _[`tls_version`](#tls_version)_
* **`tls_1_2`**: _[`tls_version`](#tls_version)_
* **`tls_1_3`**: _[`tls_version`](#tls_version)_

---

### _[`backend_config_options`](#backend_config_options)_

Set of constants, of type `u32`

Predefined constants for _[`backend_config_options`](#backend_config_options)_:

* **`reserved`** = `0x1`
* **`host_override`** = `0x2`
* **`connect_timeout`** = `0x4`
* **`first_byte_timeout`** = `0x8`
* **`between_bytes_timeout`** = `0x10`
* **`use_ssl`** = `0x20`
* **`ssl_min_version`** = `0x40`
* **`ssl_max_version`** = `0x80`
* **`cert_hostname`** = `0x100`
* **`ca_cert`** = `0x200`
* **`ciphers`** = `0x400`
* **`sni_hostname`** = `0x800`
* **`dont_pool`** = `0x1000`
* **`client_cert`** = `0x2000`
* **`grpc`** = `0x4000`

---

### _[`dynamic_backend_config`](#dynamic_backend_config)_
Structure, with the following members:

* **`host_override`**: `char8` mutable pointer
* **`host_override_len`**: `u32`
* **`connect_timeout_ms`**: `u32`
* **`first_byte_timeout_ms`**: `u32`
* **`between_bytes_timeout_ms`**: `u32`
* **`ssl_min_version`**: _[`tls_version`](#tls_version)_
* **`ssl_max_version`**: _[`tls_version`](#tls_version)_
* **`cert_hostname`**: `char8` mutable pointer
* **`cert_hostname_len`**: `u32`
* **`ca_cert`**: `char8` mutable pointer
* **`ca_cert_len`**: `u32`
* **`ciphers`**: `char8` mutable pointer
* **`ciphers_len`**: `u32`
* **`sni_hostname`**: `char8` mutable pointer
* **`sni_hostname_len`**: `u32`
* **`client_certificate`**: `char8` mutable pointer
* **`client_certificate_len`**: `u32`
* **`client_key`**: _[`secret_handle`](#secret_handle)_

---

### _[`client_cert_verify_result`](#client_cert_verify_result)_

Enumeration with tag type: `u32`, and the following members:

* **`ok`**: _[`client_cert_verify_result`](#client_cert_verify_result)_
* **`bad_certificate`**: _[`client_cert_verify_result`](#client_cert_verify_result)_
* **`certificate_revoked`**: _[`client_cert_verify_result`](#client_cert_verify_result)_
* **`certificate_expired`**: _[`client_cert_verify_result`](#client_cert_verify_result)_
* **`unknown_ca`**: _[`client_cert_verify_result`](#client_cert_verify_result)_
* **`certificate_missing`**: _[`client_cert_verify_result`](#client_cert_verify_result)_
* **`certificate_unknown`**: _[`client_cert_verify_result`](#client_cert_verify_result)_

> TLS client certificate verified result from downstream.


---

### _[`purge_options_mask`](#purge_options_mask)_

Set of constants, of type `u32`

Predefined constants for _[`purge_options_mask`](#purge_options_mask)_:

* **`soft_purge`** = `1`
* **`ret_buf`** = `2`

---

### _[`purge_options`](#purge_options)_
Structure, with the following members:

* **`ret_buf_ptr`**: `u8` mutable pointer
* **`ret_buf_len`**: `usize`
* **`ret_buf_nwritten_out`**: `usize` mutable pointer

---

### _[`send_error_detail_tag`](#send_error_detail_tag)_

Enumeration with tag type: `u32`, and the following members:

* **`uninitialized`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`ok`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`dns_timeout`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`dns_error`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`destination_not_found`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`destination_unavailable`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`destination_ip_unroutable`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`connection_refused`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`connection_terminated`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`connection_timeout`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`connection_limit_reached`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`tls_certificate_error`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`tls_configuration_error`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`http_incomplete_response`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`http_response_header_section_too_large`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`http_response_body_too_large`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`http_response_timeout`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`http_response_status_invalid`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`http_upgrade_failed`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`http_protocol_error`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`http_request_cache_key_invalid`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`http_request_uri_invalid`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`internal_error`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`tls_alert_received`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`tls_protocol_error`**: _[`send_error_detail_tag`](#send_error_detail_tag)_

---

### _[`send_error_detail_mask`](#send_error_detail_mask)_

Set of constants, of type `u32`

Predefined constants for _[`send_error_detail_mask`](#send_error_detail_mask)_:

* **`reserved`** = `0x1`
* **`dns_error_rcode`** = `0x2`
* **`dns_error_info_code`** = `0x4`
* **`tls_alert_id`** = `0x8`

> Mask representing which fields are understood by the guest, and which have been set by the host.
>
> When the guest calls hostcalls with a mask, it should set every bit in the mask that corresponds
> to a defined flag. This signals the host to write only to fields with a set bit, allowing
> forward compatibility for existing guest programs even after new fields are added to the struct.


---

### _[`send_error_detail`](#send_error_detail)_
Structure, with the following members:

* **`tag`**: _[`send_error_detail_tag`](#send_error_detail_tag)_
* **`mask`**: _[`send_error_detail_mask`](#send_error_detail_mask)_
* **`dns_error_rcode`**: `u16`
* **`dns_error_info_code`**: `u16`
* **`tls_alert_id`**: `u8`

---

### _[`blocked`](#blocked)_
Alias for `u32`.


---

### _[`rate`](#rate)_
Alias for `u32`.


---

### _[`count`](#count)_
Alias for `u32`.


---

### _[`has`](#has)_
Alias for `u32`.


---

### _[`body_length`](#body_length)_
Alias for `u64`.


---

## Functions

### [`body_downstream_get()`](#body_downstream_get)
Returned error type: _[`fastly_status`](#fastly_status)_


#### Output:

* _[`request_handle`](#request_handle)_ mutable pointer
* _[`body_handle`](#body_handle)_ mutable pointer

---

### [`cache_override_set()`](#cache_override_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`tag`**: _[`cache_override_tag`](#cache_override_tag)_
* **`ttl`**: `u32`
* **`stale_while_revalidate`**: `u32`

This function has no output.

---

### [`cache_override_v2_set()`](#cache_override_v2_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`tag`**: _[`cache_override_tag`](#cache_override_tag)_
* **`ttl`**: `u32`
* **`stale_while_revalidate`**: `u32`
* **`sk`**: `u8` mutable slice

This function has no output.

---

### [`downstream_client_ip_addr()`](#downstream_client_ip_addr)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`addr_octets_out`**: `char8` mutable pointer

#### Output:

* _[`num_bytes`](#num_bytes)_ mutable pointer

---

### [`downstream_client_h2_fingerprint()`](#downstream_client_h2_fingerprint)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h2fp_out`**: `char8` mutable pointer
* **`h2fp_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`downstream_client_request_id()`](#downstream_client_request_id)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`reqid_out`**: `char8` mutable pointer
* **`reqid_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`downstream_client_oh_fingerprint()`](#downstream_client_oh_fingerprint)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`ohfp_out`**: `char8` mutable pointer
* **`ohfp_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`downstream_tls_cipher_openssl_name()`](#downstream_tls_cipher_openssl_name)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`cipher_out`**: `char8` mutable pointer
* **`cipher_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`downstream_tls_protocol()`](#downstream_tls_protocol)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`protocol_out`**: `char8` mutable pointer
* **`protocol_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`downstream_tls_client_hello()`](#downstream_tls_client_hello)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`chello_out`**: `char8` mutable pointer
* **`chello_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`downstream_tls_raw_client_certificate()`](#downstream_tls_raw_client_certificate)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`raw_client_cert_out`**: `char8` mutable pointer
* **`raw_client_cert_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`downstream_tls_client_cert_verify_result()`](#downstream_tls_client_cert_verify_result)
Returned error type: _[`fastly_status`](#fastly_status)_


#### Output:

* _[`client_cert_verify_result`](#client_cert_verify_result)_ mutable pointer

---

### [`downstream_tls_ja3_md5()`](#downstream_tls_ja3_md5)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`cja3_md5_out`**: `char8` mutable pointer

#### Output:

* _[`num_bytes`](#num_bytes)_ mutable pointer

---

### [`downstream_tls_ja4()`](#downstream_tls_ja4)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`ja4_out`**: `char8` mutable pointer
* **`ja4_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`new()`](#new)
Returned error type: _[`fastly_status`](#fastly_status)_


#### Output:

* _[`request_handle`](#request_handle)_ mutable pointer

---

### [`header_names_get()`](#header_names_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`buf`**: `char8` mutable pointer
* **`buf_len`**: `usize`
* **`cursor`**: _[`multi_value_cursor`](#multi_value_cursor)_
* **`ending_cursor_out`**: _[`multi_value_cursor_result`](#multi_value_cursor_result)_ mutable pointer
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`original_header_names_get()`](#original_header_names_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`buf`**: `char8` mutable pointer
* **`buf_len`**: `usize`
* **`cursor`**: _[`multi_value_cursor`](#multi_value_cursor)_
* **`ending_cursor_out`**: _[`multi_value_cursor_result`](#multi_value_cursor_result)_ mutable pointer
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`original_header_count()`](#original_header_count)
Returned error type: _[`fastly_status`](#fastly_status)_


#### Output:

* _[`header_count`](#header_count)_ mutable pointer

---

### [`header_value_get()`](#header_value_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`name`**: `u8` mutable slice
* **`value`**: `char8` mutable pointer
* **`value_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`header_values_get()`](#header_values_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`name`**: `u8` mutable slice
* **`buf`**: `char8` mutable pointer
* **`buf_len`**: `usize`
* **`cursor`**: _[`multi_value_cursor`](#multi_value_cursor)_
* **`ending_cursor_out`**: _[`multi_value_cursor_result`](#multi_value_cursor_result)_ mutable pointer
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`header_values_set()`](#header_values_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`name`**: `u8` mutable slice
* **`values`**: `string`

This function has no output.

---

### [`header_insert()`](#header_insert)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`name`**: `u8` mutable slice
* **`value`**: `u8` mutable slice

This function has no output.

---

### [`header_append()`](#header_append)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`name`**: `u8` mutable slice
* **`value`**: `u8` mutable slice

This function has no output.

---

### [`header_remove()`](#header_remove)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`name`**: `u8` mutable slice

This function has no output.

---

### [`method_get()`](#method_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`buf`**: `char8` mutable pointer
* **`buf_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`method_set()`](#method_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`method`**: `string`

This function has no output.

---

### [`uri_get()`](#uri_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`buf`**: `char8` mutable pointer
* **`buf_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`uri_set()`](#uri_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`uri`**: `string`

This function has no output.

---

### [`version_get()`](#version_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_

#### Output:

* _[`http_version`](#http_version)_ mutable pointer

---

### [`version_set()`](#version_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`version`**: _[`http_version`](#http_version)_

This function has no output.

---

### [`send()`](#send)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`b`**: _[`body_handle`](#body_handle)_
* **`backend`**: `string`

#### Output:

* _[`response_handle`](#response_handle)_ mutable pointer
* _[`body_handle`](#body_handle)_ mutable pointer

---

### [`send_v2()`](#send_v2)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`b`**: _[`body_handle`](#body_handle)_
* **`backend`**: `string`
* **`error_detail`**: _[`send_error_detail`](#send_error_detail)_ mutable pointer

#### Output:

* _[`response_handle`](#response_handle)_ mutable pointer
* _[`body_handle`](#body_handle)_ mutable pointer

---

### [`send_async()`](#send_async)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`b`**: _[`body_handle`](#body_handle)_
* **`backend`**: `string`

#### Output:

* _[`pending_request_handle`](#pending_request_handle)_ mutable pointer

---

### [`send_async_streaming()`](#send_async_streaming)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`b`**: _[`body_handle`](#body_handle)_
* **`backend`**: `string`

#### Output:

* _[`pending_request_handle`](#pending_request_handle)_ mutable pointer

---

### [`pending_req_poll()`](#pending_req_poll)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`pending_request_handle`](#pending_request_handle)_

#### Output:

* _[`is_done`](#is_done)_ mutable pointer
* _[`response_handle`](#response_handle)_ mutable pointer
* _[`body_handle`](#body_handle)_ mutable pointer

---

### [`pending_req_poll_v2()`](#pending_req_poll_v2)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`pending_request_handle`](#pending_request_handle)_
* **`error_detail`**: _[`send_error_detail`](#send_error_detail)_ mutable pointer

#### Output:

* _[`is_done`](#is_done)_ mutable pointer
* _[`response_handle`](#response_handle)_ mutable pointer
* _[`body_handle`](#body_handle)_ mutable pointer

---

### [`pending_req_wait()`](#pending_req_wait)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`pending_request_handle`](#pending_request_handle)_

#### Output:

* _[`response_handle`](#response_handle)_ mutable pointer
* _[`body_handle`](#body_handle)_ mutable pointer

---

### [`pending_req_wait_v2()`](#pending_req_wait_v2)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`pending_request_handle`](#pending_request_handle)_
* **`error_detail`**: _[`send_error_detail`](#send_error_detail)_ mutable pointer

#### Output:

* _[`response_handle`](#response_handle)_ mutable pointer
* _[`body_handle`](#body_handle)_ mutable pointer

---

### [`pending_req_select()`](#pending_req_select)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`hs`**: _[`pending_request_handle`](#pending_request_handle)_ mutable slice

#### Output:

* _[`done_idx`](#done_idx)_ mutable pointer
* _[`response_handle`](#response_handle)_ mutable pointer
* _[`body_handle`](#body_handle)_ mutable pointer

---

### [`pending_req_select_v2()`](#pending_req_select_v2)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`hs`**: _[`pending_request_handle`](#pending_request_handle)_ mutable slice
* **`error_detail`**: _[`send_error_detail`](#send_error_detail)_ mutable pointer

#### Output:

* _[`done_idx`](#done_idx)_ mutable pointer
* _[`response_handle`](#response_handle)_ mutable pointer
* _[`body_handle`](#body_handle)_ mutable pointer

---

### [`fastly_key_is_valid()`](#fastly_key_is_valid)
Returned error type: _[`fastly_status`](#fastly_status)_


#### Output:

* _[`is_valid`](#is_valid)_ mutable pointer

> Returns whether or not the original client request arrived with a
> Fastly-Key belonging to a user with the rights to purge content on this
> service.


---

### [`close()`](#close)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_

This function has no output.

---

### [`auto_decompress_response_set()`](#auto_decompress_response_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`encodings`**: _[`content_encodings`](#content_encodings)_

This function has no output.

---

### [`upgrade_websocket()`](#upgrade_websocket)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`backend_name`**: `string`

This function has no output.

---

### [`redirect_to_websocket_proxy()`](#redirect_to_websocket_proxy)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`backend_name`**: `string`

This function has no output.

---

### [`redirect_to_grip_proxy()`](#redirect_to_grip_proxy)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`backend_name`**: `string`

This function has no output.

---

### [`redirect_to_websocket_proxy_v2()`](#redirect_to_websocket_proxy_v2)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`backend_name`**: `string`

This function has no output.

---

### [`redirect_to_grip_proxy_v2()`](#redirect_to_grip_proxy_v2)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`backend_name`**: `string`

This function has no output.

---

### [`framing_headers_mode_set()`](#framing_headers_mode_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`request_handle`](#request_handle)_
* **`mode`**: _[`framing_headers_mode`](#framing_headers_mode)_

This function has no output.

> Adjust how this requests's framing headers are determined.


---

### [`register_dynamic_backend()`](#register_dynamic_backend)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`name_prefix`**: `string`
* **`target`**: `string`
* **`backend_config_mask`**: _[`backend_config_options`](#backend_config_options)_
* **`backend_configuration`**: _[`dynamic_backend_config`](#dynamic_backend_config)_ mutable pointer

This function has no output.

> Create a backend for later use


---

