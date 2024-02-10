
# Module: typenames

## Table of contents

### Types list:

[**[All](#types)**] - [_[`fastly_status`](#fastly_status)_] - [_[`http_version`](#http_version)_] - [_[`http_status`](#http_status)_] - [_[`body_write_end`](#body_write_end)_] - [_[`body_handle`](#body_handle)_] - [_[`request_handle`](#request_handle)_] - [_[`response_handle`](#response_handle)_] - [_[`pending_request_handle`](#pending_request_handle)_] - [_[`endpoint_handle`](#endpoint_handle)_] - [_[`dictionary_handle`](#dictionary_handle)_] - [_[`object_store_handle`](#object_store_handle)_] - [_[`pending_object_store_lookup_handle`](#pending_object_store_lookup_handle)_] - [_[`pending_object_store_insert_handle`](#pending_object_store_insert_handle)_] - [_[`pending_object_store_delete_handle`](#pending_object_store_delete_handle)_] - [_[`secret_store_handle`](#secret_store_handle)_] - [_[`secret_handle`](#secret_handle)_] - [_[`async_item_handle`](#async_item_handle)_] - [_[`multi_value_cursor`](#multi_value_cursor)_] - [_[`multi_value_cursor_result`](#multi_value_cursor_result)_] - [_[`cache_override_tag`](#cache_override_tag)_] - [_[`num_bytes`](#num_bytes)_] - [_[`header_count`](#header_count)_] - [_[`is_done`](#is_done)_] - [_[`done_idx`](#done_idx)_] - [_[`is_valid`](#is_valid)_] - [_[`inserted`](#inserted)_] - [_[`ready_idx`](#ready_idx)_] - [_[`port`](#port)_] - [_[`timeout_ms`](#timeout_ms)_] - [_[`backend_exists`](#backend_exists)_] - [_[`is_dynamic`](#is_dynamic)_] - [_[`is_ssl`](#is_ssl)_] - [_[`backend_health`](#backend_health)_] - [_[`content_encodings`](#content_encodings)_] - [_[`framing_headers_mode`](#framing_headers_mode)_] - [_[`http_keepalive_mode`](#http_keepalive_mode)_] - [_[`tls_version`](#tls_version)_] - [_[`backend_config_options`](#backend_config_options)_] - [_[`dynamic_backend_config`](#dynamic_backend_config)_] - [_[`client_cert_verify_result`](#client_cert_verify_result)_] - [_[`purge_options_mask`](#purge_options_mask)_] - [_[`purge_options`](#purge_options)_] - [_[`send_error_detail_tag`](#send_error_detail_tag)_] - [_[`send_error_detail_mask`](#send_error_detail_mask)_] - [_[`send_error_detail`](#send_error_detail)_] - [_[`blocked`](#blocked)_] - [_[`rate`](#rate)_] - [_[`count`](#count)_] - [_[`has`](#has)_] - [_[`body_length`](#body_length)_]

### Functions list:

[**[All](#functions)**]

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

