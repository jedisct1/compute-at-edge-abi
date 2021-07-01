
# Module: fastly_dictionary

## Table of contents

### Types list:

[**[All](#types)**] - [_[`fastly_status`](#fastly_status)_] - [_[`http_version`](#http_version)_] - [_[`http_status`](#http_status)_] - [_[`body_write_end`](#body_write_end)_] - [_[`body_handle`](#body_handle)_] - [_[`request_handle`](#request_handle)_] - [_[`response_handle`](#response_handle)_] - [_[`pending_request_handle`](#pending_request_handle)_] - [_[`endpoint_handle`](#endpoint_handle)_] - [_[`dictionary_handle`](#dictionary_handle)_] - [_[`multi_value_cursor`](#multi_value_cursor)_] - [_[`multi_value_cursor_result`](#multi_value_cursor_result)_] - [_[`cache_override_tag`](#cache_override_tag)_] - [_[`num_bytes`](#num_bytes)_] - [_[`header_count`](#header_count)_] - [_[`is_done`](#is_done)_] - [_[`done_idx`](#done_idx)_]

### Functions list:

[**[All](#functions)**] - [[`open()`](#open)] - [[`get()`](#get)]

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

### [`open()`](#open)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`name`**: `string`

#### Output:

* _[`dictionary_handle`](#dictionary_handle)_ mutable pointer

---

### [`get()`](#get)
Returned error type: _[`fastly_status`](#fastly_status)_

#### Input:

* **`h`**: _[`dictionary_handle`](#dictionary_handle)_
* **`key`**: `string`
* **`value`**: `char8` mutable pointer
* **`value_max_len`**: `usize`

#### Output:

* _[`num_bytes`](#num_bytes)_ mutable pointer

---
