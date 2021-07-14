
# Module: fastly_http_resp

## Table of contents

### Types list:

[**[All](#types)**] - [_[`fastly_status`](#fastly_status)_] - [_[`http_version`](#http_version)_] - [_[`http_status`](#http_status)_] - [_[`body_write_end`](#body_write_end)_] - [_[`body_handle`](#body_handle)_] - [_[`request_handle`](#request_handle)_] - [_[`response_handle`](#response_handle)_] - [_[`pending_request_handle`](#pending_request_handle)_] - [_[`endpoint_handle`](#endpoint_handle)_] - [_[`dictionary_handle`](#dictionary_handle)_] - [_[`multi_value_cursor`](#multi_value_cursor)_] - [_[`multi_value_cursor_result`](#multi_value_cursor_result)_] - [_[`cache_override_tag`](#cache_override_tag)_] - [_[`num_bytes`](#num_bytes)_] - [_[`header_count`](#header_count)_] - [_[`is_done`](#is_done)_] - [_[`done_idx`](#done_idx)_]

### Functions list:

[**[All](#functions)**] - [[`new()`](#new)] - [[`header_names_get()`](#header_names_get)] - [[`header_value_get()`](#header_value_get)] - [[`header_values_get()`](#header_values_get)] - [[`header_values_set()`](#header_values_set)] - [[`header_insert()`](#header_insert)] - [[`header_append()`](#header_append)] - [[`header_remove()`](#header_remove)] - [[`version_get()`](#version_get)] - [[`version_set()`](#version_set)] - [[`send_downstream()`](#send_downstream)] - [[`status_get()`](#status_get)] - [[`status_set()`](#status_set)] - [[`close()`](#close)]

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

---

### _[`http_version`](#http_version)_

Enumeration with tag type: `u32`, and the following members:

* **`http_09`**: _[`http_version`](#http_version)_
* **`http_10`**: _[`http_version`](#http_version)_
* **`http_11`**: _[`http_version`](#http_version)_
* **`h2`**: _[`http_version`](#http_version)_
* **`h3`**: _[`http_version`](#http_version)_

---

### _[`http_status`](#http_status)_
Alias for `u16`.


---

### _[`body_write_end`](#body_write_end)_

Enumeration with tag type: `u32`, and the following members:

* **`back`**: _[`body_write_end`](#body_write_end)_
* **`front`**: _[`body_write_end`](#body_write_end)_

---

### _[`body_handle`](#body_handle)_
Alias for `handle`.


---

### _[`request_handle`](#request_handle)_
Alias for `handle`.


---

### _[`response_handle`](#response_handle)_
Alias for `handle`.


---

### _[`pending_request_handle`](#pending_request_handle)_
Alias for `handle`.


---

### _[`endpoint_handle`](#endpoint_handle)_
Alias for `handle`.


---

### _[`dictionary_handle`](#dictionary_handle)_
Alias for `handle`.


---

### _[`multi_value_cursor`](#multi_value_cursor)_
Alias for `u32`.


---

### _[`multi_value_cursor_result`](#multi_value_cursor_result)_
Alias for `i64`.


---

### _[`cache_override_tag`](#cache_override_tag)_

Set of constants, of type `u32`

Predefined constants for _[`cache_override_tag`](#cache_override_tag)_:

* **`none`** = `0x1`
* **`pass`** = `0x2`
* **`ttl`** = `0x4`
* **`stale_while_revalidate`** = `0x8`
* **`pci`** = `0x10`

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

## Functions

### [`new()`](#new)
Returned error type: _[`fastly_status`](#fastly_status)_


#### Output:

* _[`response_handle`](#response_handle)_ mutable pointer

---

### [`header_names_get()`](#header_names_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_
* **`buf`**: `char8` mutable pointer
* **`buf_len`**: `usize`
* **`cursor`**: _[`multi_value_cursor`](#multi_value_cursor)_
* **`ending_cursor_out`**: _[`multi_value_cursor_result`](#multi_value_cursor_result)_ mutable pointer
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`header_value_get()`](#header_value_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_
* **`name`**: `u8` mutable slice
* **`value`**: `char8` mutable pointer
* **`value_max_len`**: `usize`
* **`nwritten_out`**: `usize` mutable pointer

This function has no output.

---

### [`header_values_get()`](#header_values_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_
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

* **`h`**: _[`response_handle`](#response_handle)_
* **`name`**: `u8` mutable slice
* **`values`**: `string`

This function has no output.

---

### [`header_insert()`](#header_insert)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_
* **`name`**: `u8` mutable slice
* **`value`**: `u8` mutable slice

This function has no output.

---

### [`header_append()`](#header_append)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_
* **`name`**: `u8` mutable slice
* **`value`**: `u8` mutable slice

This function has no output.

---

### [`header_remove()`](#header_remove)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_
* **`name`**: `u8` mutable slice

This function has no output.

---

### [`version_get()`](#version_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_

#### Output:

* _[`http_version`](#http_version)_ mutable pointer

---

### [`version_set()`](#version_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_
* **`version`**: _[`http_version`](#http_version)_

This function has no output.

---

### [`send_downstream()`](#send_downstream)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_
* **`b`**: _[`body_handle`](#body_handle)_
* **`streaming`**: `u32`

This function has no output.

---

### [`status_get()`](#status_get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_

#### Output:

* _[`http_status`](#http_status)_ mutable pointer

---

### [`status_set()`](#status_set)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_
* **`status`**: _[`http_status`](#http_status)_

This function has no output.

---

### [`close()`](#close)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`response_handle`](#response_handle)_

This function has no output.

---

