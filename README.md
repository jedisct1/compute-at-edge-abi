# Fastly Compute ABI

This repository contains `witx` definitions for the Fastly Compute platform ABI.

This fork includes definitions that have been [updated](https://github.com/jedisct1/compute-at-edge-abi/tree/witx-next/witx-next)
to be compatible with the [witx-codegen](https://github.com/jedisct1/witx-codegen) code generator.

### [Documentation](https://github.com/jedisct1/compute-at-edge-abi/tree/witx-next/doc)

* [fastly_abi](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_abi.witx.md)
* [fastly_async_io](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_async_io.witx.md)
* [fastly_backend](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_backend.witx.md)
* [fastly_cache](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_cache.witx.md)
* [fastly_config_store](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_config_store.witx.md)
* [fastly_device_detection](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_device_detection.witx.md)
* [fastly_dictionary](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_dictionary.witx.md)
* [fastly_erl](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_erl.witx.md)
* [fastly_geo](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_geo.witx.md)
* [fastly_http_body](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_http_body.witx.md)
* [fastly_http_req](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_http_req.witx.md)
* [fastly_http_resp](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_http_resp.witx.md)
* [fastly_kv](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_kv.witx.md)
* [fastly_log](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_log.witx.md)
* [fastly_object_store](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_object_store.witx.md)
* [fastly_purge](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_purge.witx.md)
* [fastly_secret_store](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_secret_store.witx.md)
* [fastly_uap](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_uap.witx.md)

### API overview

```text
---------------------- Module: [typenames] ----------------------

enum fastly_status: (tag: u32)
    - ok: 0
    - error: 1
    - inval: 2
    - badf: 3
    - buflen: 4
    - unsupported: 5
    - badalign: 6
    - httpinvalid: 7
    - httpuser: 8
    - httpincomplete: 9
    - none: 10
    - httpheadtoolarge: 11
    - httpinvalidstatus: 12
    - limitexceeded: 13
    - again: 14

enum http_version: (tag: u32)
    - http_09: 0
    - http_10: 1
    - http_11: 2
    - h2: 3
    - h3: 4

alias http_status = u16

enum body_write_end: (tag: u32)
    - back: 0
    - front: 1

alias body_handle = handle

alias request_handle = handle

alias response_handle = handle

alias pending_request_handle = handle

alias endpoint_handle = handle

alias dictionary_handle = handle

alias object_store_handle = handle

alias pending_object_store_lookup_handle = handle

alias pending_object_store_insert_handle = handle

alias pending_object_store_delete_handle = handle

alias secret_store_handle = handle

alias secret_handle = handle

alias async_item_handle = handle

alias multi_value_cursor = u32

alias multi_value_cursor_result = i64

constants cache_override_tag: (type: u32)
predefined constants for cache_override_tag:
    - pass = 0x1
    - ttl = 0x2
    - stale_while_revalidate = 0x4
    - pci = 0x8

alias num_bytes = usize

alias header_count = u32

alias is_done = u32

alias done_idx = u32

alias is_valid = u32

alias inserted = u32

alias ready_idx = u32

alias port = u16

alias timeout_ms = u32

alias backend_exists = u32

alias is_dynamic = u32

alias is_ssl = u32

enum backend_health: (tag: u32)
    - unknown: 0
    - healthy: 1
    - unhealthy: 2

constants content_encodings: (type: u32)
predefined constants for content_encodings:
    - gzip = 1

enum framing_headers_mode: (tag: u32)
    - automatic: 0
    - manually_from_headers: 1

enum http_keepalive_mode: (tag: u32)
    - automatic: 0
    - no_keepalive: 1

enum tls_version: (tag: u32)
    - tls_1: 0
    - tls_1_1: 1
    - tls_1_2: 2
    - tls_1_3: 3

constants backend_config_options: (type: u32)
predefined constants for backend_config_options:
    - reserved = 0x1
    - host_override = 0x2
    - connect_timeout = 0x4
    - first_byte_timeout = 0x8
    - between_bytes_timeout = 0x10
    - use_ssl = 0x20
    - ssl_min_version = 0x40
    - ssl_max_version = 0x80
    - cert_hostname = 0x100
    - ca_cert = 0x200
    - ciphers = 0x400
    - sni_hostname = 0x800
    - dont_pool = 0x1000
    - client_cert = 0x2000
    - grpc = 0x4000

struct dynamic_backend_config:
    - host_override: mut_ptr<char8>
    - host_override_len: u32
    - connect_timeout_ms: u32
    - first_byte_timeout_ms: u32
    - between_bytes_timeout_ms: u32
    - ssl_min_version: tls_version
    - ssl_max_version: tls_version
    - cert_hostname: mut_ptr<char8>
    - cert_hostname_len: u32
    - ca_cert: mut_ptr<char8>
    - ca_cert_len: u32
    - ciphers: mut_ptr<char8>
    - ciphers_len: u32
    - sni_hostname: mut_ptr<char8>
    - sni_hostname_len: u32
    - client_certificate: mut_ptr<char8>
    - client_certificate_len: u32
    - client_key: secret_handle

enum client_cert_verify_result: (tag: u32)
    - ok: 0
    - bad_certificate: 1
    - certificate_revoked: 2
    - certificate_expired: 3
    - unknown_ca: 4
    - certificate_missing: 5
    - certificate_unknown: 6

constants purge_options_mask: (type: u32)
predefined constants for purge_options_mask:
    - soft_purge = 1
    - ret_buf = 2

struct purge_options:
    - ret_buf_ptr: mut_ptr<u8>
    - ret_buf_len: usize
    - ret_buf_nwritten_out: mut_ptr<usize>

enum send_error_detail_tag: (tag: u32)
    - uninitialized: 0
    - ok: 1
    - dns_timeout: 2
    - dns_error: 3
    - destination_not_found: 4
    - destination_unavailable: 5
    - destination_ip_unroutable: 6
    - connection_refused: 7
    - connection_terminated: 8
    - connection_timeout: 9
    - connection_limit_reached: 10
    - tls_certificate_error: 11
    - tls_configuration_error: 12
    - http_incomplete_response: 13
    - http_response_header_section_too_large: 14
    - http_response_body_too_large: 15
    - http_response_timeout: 16
    - http_response_status_invalid: 17
    - http_upgrade_failed: 18
    - http_protocol_error: 19
    - http_request_cache_key_invalid: 20
    - http_request_uri_invalid: 21
    - internal_error: 22
    - tls_alert_received: 23
    - tls_protocol_error: 24

constants send_error_detail_mask: (type: u32)
predefined constants for send_error_detail_mask:
    - reserved = 0x1
    - dns_error_rcode = 0x2
    - dns_error_info_code = 0x4
    - tls_alert_id = 0x8

struct send_error_detail:
    - tag: send_error_detail_tag
    - mask: send_error_detail_mask
    - dns_error_rcode: u16
    - dns_error_info_code: u16
    - tls_alert_id: u8

alias blocked = u32

alias rate = u32

alias count = u32

alias has = u32

alias body_length = u64


---------------------- Module: [fastly_abi] ----------------------

function init(): fastly_status
    - Input:
        - abi_version: u64
    - No output


---------------------- Module: [fastly_async_io] ----------------------

function select(): fastly_status
    - Input:
        - hs: mut_slice<async_item_handle>
        - timeout_ms: u32
    - Output:
        - mut_ptr<ready_idx>

function is_ready(): fastly_status
    - Input:
        - handle: async_item_handle
    - Output:
        - mut_ptr<is_done>


---------------------- Module: [fastly_backend] ----------------------

function exists(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<backend_exists>

function is_healthy(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<backend_health>

function is_dynamic(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<is_dynamic>

function get_host(): fastly_status
    - Input:
        - backend: string
        - value: mut_ptr<char8>
        - value_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function get_override_host(): fastly_status
    - Input:
        - backend: string
        - value: mut_ptr<char8>
        - value_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function get_port(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<port>

function get_connect_timeout_ms(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<timeout_ms>

function get_first_byte_timeout_ms(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<timeout_ms>

function get_between_bytes_timeout_ms(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<timeout_ms>

function is_ssl(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<is_ssl>

function get_ssl_min_version(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<tls_version>

function get_ssl_max_version(): fastly_status
    - Input:
        - backend: string
    - Output:
        - mut_ptr<tls_version>


---------------------- Module: [fastly_cache] ----------------------

alias cache_handle = handle

alias cache_object_length = u64

alias cache_duration_ns = u64

alias cache_hit_count = u64

struct cache_lookup_options:
    - request_headers: request_handle

constants cache_lookup_options_mask: (type: u32)
predefined constants for cache_lookup_options_mask:
    - reserved = 1
    - request_headers = 2

struct cache_write_options:
    - max_age_ns: cache_duration_ns
    - request_headers: request_handle
    - vary_rule_ptr: mut_ptr<char8>
    - vary_rule_len: usize
    - initial_age_ns: cache_duration_ns
    - stale_while_revalidate_ns: cache_duration_ns
    - surrogate_keys_ptr: mut_ptr<char8>
    - surrogate_keys_len: usize
    - length: cache_object_length
    - user_metadata_ptr: mut_ptr<u8>
    - user_metadata_len: usize

constants cache_write_options_mask: (type: u32)
predefined constants for cache_write_options_mask:
    - reserved = 0x1
    - request_headers = 0x2
    - vary_rule = 0x4
    - initial_age_ns = 0x8
    - stale_while_revalidate_ns = 0x10
    - surrogate_keys = 0x20
    - length = 0x40
    - user_metadata = 0x80
    - sensitive_data = 0x100

struct cache_get_body_options:
    - from: u64
    - to: u64

constants cache_get_body_options_mask: (type: u32)
predefined constants for cache_get_body_options_mask:
    - reserved = 0x1
    - from = 0x2
    - to = 0x4

constants cache_lookup_state: (type: u32)
predefined constants for cache_lookup_state:
    - found = 0x1
    - usable = 0x2
    - stale = 0x4
    - must_insert_or_update = 0x8

function lookup(): fastly_status
    - Input:
        - cache_key: mut_slice<u8>
        - options_mask: cache_lookup_options_mask
        - options: mut_ptr<cache_lookup_options>
    - Output:
        - mut_ptr<cache_handle>

function insert(): fastly_status
    - Input:
        - cache_key: mut_slice<u8>
        - options_mask: cache_write_options_mask
        - options: mut_ptr<cache_write_options>
    - Output:
        - mut_ptr<body_handle>

function transaction_lookup(): fastly_status
    - Input:
        - cache_key: mut_slice<u8>
        - options_mask: cache_lookup_options_mask
        - options: mut_ptr<cache_lookup_options>
    - Output:
        - mut_ptr<cache_handle>

function transaction_insert(): fastly_status
    - Input:
        - handle: cache_handle
        - options_mask: cache_write_options_mask
        - options: mut_ptr<cache_write_options>
    - Output:
        - mut_ptr<body_handle>

function transaction_insert_and_stream_back(): fastly_status
    - Input:
        - handle: cache_handle
        - options_mask: cache_write_options_mask
        - options: mut_ptr<cache_write_options>
    - Output:
        - mut_ptr<body_handle>
        - mut_ptr<cache_handle>

function transaction_update(): fastly_status
    - Input:
        - handle: cache_handle
        - options_mask: cache_write_options_mask
        - options: mut_ptr<cache_write_options>
    - No output

function transaction_cancel(): fastly_status
    - Input:
        - handle: cache_handle
    - No output

function close(): fastly_status
    - Input:
        - handle: cache_handle
    - No output

function get_state(): fastly_status
    - Input:
        - handle: cache_handle
    - Output:
        - mut_ptr<cache_lookup_state>

function get_user_metadata(): fastly_status
    - Input:
        - handle: cache_handle
        - user_metadata_out_ptr: mut_ptr<u8>
        - user_metadata_out_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function get_body(): fastly_status
    - Input:
        - handle: cache_handle
        - options_mask: cache_get_body_options_mask
        - options: cache_get_body_options
    - Output:
        - mut_ptr<body_handle>

function get_length(): fastly_status
    - Input:
        - handle: cache_handle
    - Output:
        - mut_ptr<cache_object_length>

function get_max_age_ns(): fastly_status
    - Input:
        - handle: cache_handle
    - Output:
        - mut_ptr<cache_duration_ns>

function get_stale_while_revalidate_ns(): fastly_status
    - Input:
        - handle: cache_handle
    - Output:
        - mut_ptr<cache_duration_ns>

function get_age_ns(): fastly_status
    - Input:
        - handle: cache_handle
    - Output:
        - mut_ptr<cache_duration_ns>

function get_hits(): fastly_status
    - Input:
        - handle: cache_handle
    - Output:
        - mut_ptr<cache_hit_count>


---------------------- Module: [fastly_config_store] ----------------------

alias config_store_handle = handle

function open(): fastly_status
    - Input:
        - name: string
    - Output:
        - mut_ptr<config_store_handle>

function get(): fastly_status
    - Input:
        - h: config_store_handle
        - key: string
        - value: mut_ptr<char8>
        - value_max_len: usize
    - Output:
        - mut_ptr<num_bytes>


---------------------- Module: [fastly_device_detection] ----------------------

function lookup(): fastly_status
    - Input:
        - user_agent: string
        - buf: mut_ptr<char8>
        - buf_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output


---------------------- Module: [fastly_dictionary] ----------------------

function open(): fastly_status
    - Input:
        - name: string
    - Output:
        - mut_ptr<dictionary_handle>

function get(): fastly_status
    - Input:
        - h: dictionary_handle
        - key: string
        - value: mut_ptr<char8>
        - value_max_len: usize
    - Output:
        - mut_ptr<num_bytes>


---------------------- Module: [fastly_dns] ----------------------

alias dns_lookup_handle = handle

function lookup_addr(): fastly_status
    - Input:
        - name: string
    - Output:
        - mut_ptr<dns_lookup_handle>

function lookup_reverse(): fastly_status
    - Input:
        - ip: string
    - Output:
        - mut_ptr<dns_lookup_handle>

function lookup_txt(): fastly_status
    - Input:
        - name: string
    - Output:
        - mut_ptr<dns_lookup_handle>

function lookup_wait(): fastly_status
    - Input:
        - handle: dns_lookup_handle
        - buf: mut_ptr<char8>
        - buf_len: usize
        - cursor: multi_value_cursor
        - ending_cursor_out: mut_ptr<multi_value_cursor_result>
        - nwritten_out: mut_ptr<usize>
    - No output

function lookup_raw(): fastly_status
    - Input:
        - query: ptr<char8>
        - query_len: usize
    - Output:
        - mut_ptr<dns_lookup_handle>

function lookup_wait_raw(): fastly_status
    - Input:
        - handle: dns_lookup_handle
        - response: mut_ptr<char8>
        - response_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output


---------------------- Module: [fastly_erl] ----------------------

function check_rate(): fastly_status
    - Input:
        - rc: string
        - entry: string
        - delta: u32
        - window: u32
        - limit: u32
        - pb: string
        - ttl: u32
    - Output:
        - mut_ptr<blocked>

function ratecounter_increment(): fastly_status
    - Input:
        - rc: string
        - entry: string
        - delta: u32
    - No output

function ratecounter_lookup_rate(): fastly_status
    - Input:
        - rc: string
        - entry: string
        - window: u32
    - Output:
        - mut_ptr<rate>

function ratecounter_lookup_count(): fastly_status
    - Input:
        - rc: string
        - entry: string
        - duration: u32
    - Output:
        - mut_ptr<count>

function penaltybox_add(): fastly_status
    - Input:
        - pb: string
        - entry: string
        - ttl: u32
    - No output

function penaltybox_has(): fastly_status
    - Input:
        - pb: string
        - entry: string
    - Output:
        - mut_ptr<has>


---------------------- Module: [fastly_geo] ----------------------

function lookup(): fastly_status
    - Input:
        - addr_octets: ptr<char8>
        - addr_len: usize
        - buf: mut_ptr<char8>
        - buf_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output


---------------------- Module: [fastly_http_body] ----------------------

function append(): fastly_status
    - Input:
        - dest: body_handle
        - src: body_handle
    - No output

function new(): fastly_status
    - Output:
        - mut_ptr<body_handle>

function read(): fastly_status
    - Input:
        - h: body_handle
        - buf: mut_ptr<u8>
        - buf_len: usize
    - Output:
        - mut_ptr<num_bytes>

function write(): fastly_status
    - Input:
        - h: body_handle
        - buf: mut_slice<u8>
        - end: body_write_end
    - Output:
        - mut_ptr<num_bytes>

function close(): fastly_status
    - Input:
        - h: body_handle
    - No output

function abandon(): fastly_status
    - Input:
        - h: body_handle
    - No output

function trailer_append(): fastly_status
    - Input:
        - h: body_handle
        - name: mut_slice<u8>
        - value: mut_slice<u8>
    - No output

function trailer_names_get(): fastly_status
    - Input:
        - h: body_handle
        - buf: mut_ptr<char8>
        - buf_len: usize
        - cursor: multi_value_cursor
        - ending_cursor_out: mut_ptr<multi_value_cursor_result>
        - nwritten_out: mut_ptr<usize>
    - No output

function trailer_value_get(): fastly_status
    - Input:
        - h: body_handle
        - name: mut_slice<u8>
        - value: mut_ptr<char8>
        - value_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function trailer_values_get(): fastly_status
    - Input:
        - h: body_handle
        - name: mut_slice<u8>
        - buf: mut_ptr<char8>
        - buf_len: usize
        - cursor: multi_value_cursor
        - ending_cursor_out: mut_ptr<multi_value_cursor_result>
        - nwritten_out: mut_ptr<usize>
    - No output

function known_length(): fastly_status
    - Input:
        - h: body_handle
    - Output:
        - mut_ptr<body_length>


---------------------- Module: [fastly_http_req] ----------------------

function body_downstream_get(): fastly_status
    - Output:
        - mut_ptr<request_handle>
        - mut_ptr<body_handle>

function cache_override_set(): fastly_status
    - Input:
        - h: request_handle
        - tag: cache_override_tag
        - ttl: u32
        - stale_while_revalidate: u32
    - No output

function cache_override_v2_set(): fastly_status
    - Input:
        - h: request_handle
        - tag: cache_override_tag
        - ttl: u32
        - stale_while_revalidate: u32
        - sk: mut_slice<u8>
    - No output

function downstream_client_ip_addr(): fastly_status
    - Input:
        - addr_octets_out: mut_ptr<char8>
    - Output:
        - mut_ptr<num_bytes>

function downstream_client_h2_fingerprint(): fastly_status
    - Input:
        - h2fp_out: mut_ptr<char8>
        - h2fp_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function downstream_client_request_id(): fastly_status
    - Input:
        - reqid_out: mut_ptr<char8>
        - reqid_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function downstream_client_oh_fingerprint(): fastly_status
    - Input:
        - ohfp_out: mut_ptr<char8>
        - ohfp_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function downstream_tls_cipher_openssl_name(): fastly_status
    - Input:
        - cipher_out: mut_ptr<char8>
        - cipher_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function downstream_tls_protocol(): fastly_status
    - Input:
        - protocol_out: mut_ptr<char8>
        - protocol_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function downstream_tls_client_hello(): fastly_status
    - Input:
        - chello_out: mut_ptr<char8>
        - chello_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function downstream_tls_raw_client_certificate(): fastly_status
    - Input:
        - raw_client_cert_out: mut_ptr<char8>
        - raw_client_cert_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function downstream_tls_client_cert_verify_result(): fastly_status
    - Output:
        - mut_ptr<client_cert_verify_result>

function downstream_tls_ja3_md5(): fastly_status
    - Input:
        - cja3_md5_out: mut_ptr<char8>
    - Output:
        - mut_ptr<num_bytes>

function downstream_tls_ja4(): fastly_status
    - Input:
        - ja4_out: mut_ptr<char8>
        - ja4_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function new(): fastly_status
    - Output:
        - mut_ptr<request_handle>

function header_names_get(): fastly_status
    - Input:
        - h: request_handle
        - buf: mut_ptr<char8>
        - buf_len: usize
        - cursor: multi_value_cursor
        - ending_cursor_out: mut_ptr<multi_value_cursor_result>
        - nwritten_out: mut_ptr<usize>
    - No output

function original_header_names_get(): fastly_status
    - Input:
        - buf: mut_ptr<char8>
        - buf_len: usize
        - cursor: multi_value_cursor
        - ending_cursor_out: mut_ptr<multi_value_cursor_result>
        - nwritten_out: mut_ptr<usize>
    - No output

function original_header_count(): fastly_status
    - Output:
        - mut_ptr<header_count>

function header_value_get(): fastly_status
    - Input:
        - h: request_handle
        - name: mut_slice<u8>
        - value: mut_ptr<char8>
        - value_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function header_values_get(): fastly_status
    - Input:
        - h: request_handle
        - name: mut_slice<u8>
        - buf: mut_ptr<char8>
        - buf_len: usize
        - cursor: multi_value_cursor
        - ending_cursor_out: mut_ptr<multi_value_cursor_result>
        - nwritten_out: mut_ptr<usize>
    - No output

function header_values_set(): fastly_status
    - Input:
        - h: request_handle
        - name: mut_slice<u8>
        - values: string
    - No output

function header_insert(): fastly_status
    - Input:
        - h: request_handle
        - name: mut_slice<u8>
        - value: mut_slice<u8>
    - No output

function header_append(): fastly_status
    - Input:
        - h: request_handle
        - name: mut_slice<u8>
        - value: mut_slice<u8>
    - No output

function header_remove(): fastly_status
    - Input:
        - h: request_handle
        - name: mut_slice<u8>
    - No output

function method_get(): fastly_status
    - Input:
        - h: request_handle
        - buf: mut_ptr<char8>
        - buf_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function method_set(): fastly_status
    - Input:
        - h: request_handle
        - method: string
    - No output

function uri_get(): fastly_status
    - Input:
        - h: request_handle
        - buf: mut_ptr<char8>
        - buf_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function uri_set(): fastly_status
    - Input:
        - h: request_handle
        - uri: string
    - No output

function version_get(): fastly_status
    - Input:
        - h: request_handle
    - Output:
        - mut_ptr<http_version>

function version_set(): fastly_status
    - Input:
        - h: request_handle
        - version: http_version
    - No output

function send(): fastly_status
    - Input:
        - h: request_handle
        - b: body_handle
        - backend: string
    - Output:
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function send_v2(): fastly_status
    - Input:
        - h: request_handle
        - b: body_handle
        - backend: string
        - error_detail: mut_ptr<send_error_detail>
    - Output:
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function send_async(): fastly_status
    - Input:
        - h: request_handle
        - b: body_handle
        - backend: string
    - Output:
        - mut_ptr<pending_request_handle>

function send_async_streaming(): fastly_status
    - Input:
        - h: request_handle
        - b: body_handle
        - backend: string
    - Output:
        - mut_ptr<pending_request_handle>

function pending_req_poll(): fastly_status
    - Input:
        - h: pending_request_handle
    - Output:
        - mut_ptr<is_done>
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function pending_req_poll_v2(): fastly_status
    - Input:
        - h: pending_request_handle
        - error_detail: mut_ptr<send_error_detail>
    - Output:
        - mut_ptr<is_done>
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function pending_req_wait(): fastly_status
    - Input:
        - h: pending_request_handle
    - Output:
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function pending_req_wait_v2(): fastly_status
    - Input:
        - h: pending_request_handle
        - error_detail: mut_ptr<send_error_detail>
    - Output:
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function pending_req_select(): fastly_status
    - Input:
        - hs: mut_slice<pending_request_handle>
    - Output:
        - mut_ptr<done_idx>
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function pending_req_select_v2(): fastly_status
    - Input:
        - hs: mut_slice<pending_request_handle>
        - error_detail: mut_ptr<send_error_detail>
    - Output:
        - mut_ptr<done_idx>
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function fastly_key_is_valid(): fastly_status
    - Output:
        - mut_ptr<is_valid>

function close(): fastly_status
    - Input:
        - h: request_handle
    - No output

function auto_decompress_response_set(): fastly_status
    - Input:
        - h: request_handle
        - encodings: content_encodings
    - No output

function upgrade_websocket(): fastly_status
    - Input:
        - backend_name: string
    - No output

function redirect_to_websocket_proxy(): fastly_status
    - Input:
        - backend_name: string
    - No output

function redirect_to_grip_proxy(): fastly_status
    - Input:
        - backend_name: string
    - No output

function redirect_to_websocket_proxy_v2(): fastly_status
    - Input:
        - h: request_handle
        - backend_name: string
    - No output

function redirect_to_grip_proxy_v2(): fastly_status
    - Input:
        - h: request_handle
        - backend_name: string
    - No output

function framing_headers_mode_set(): fastly_status
    - Input:
        - h: request_handle
        - mode: framing_headers_mode
    - No output

function register_dynamic_backend(): fastly_status
    - Input:
        - name_prefix: string
        - target: string
        - backend_config_mask: backend_config_options
        - backend_configuration: mut_ptr<dynamic_backend_config>
    - No output


---------------------- Module: [fastly_http_resp] ----------------------

function new(): fastly_status
    - Output:
        - mut_ptr<response_handle>

function header_names_get(): fastly_status
    - Input:
        - h: response_handle
        - buf: mut_ptr<char8>
        - buf_len: usize
        - cursor: multi_value_cursor
        - ending_cursor_out: mut_ptr<multi_value_cursor_result>
        - nwritten_out: mut_ptr<usize>
    - No output

function header_value_get(): fastly_status
    - Input:
        - h: response_handle
        - name: mut_slice<u8>
        - value: mut_ptr<char8>
        - value_max_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function header_values_get(): fastly_status
    - Input:
        - h: response_handle
        - name: mut_slice<u8>
        - buf: mut_ptr<char8>
        - buf_len: usize
        - cursor: multi_value_cursor
        - ending_cursor_out: mut_ptr<multi_value_cursor_result>
        - nwritten_out: mut_ptr<usize>
    - No output

function header_values_set(): fastly_status
    - Input:
        - h: response_handle
        - name: mut_slice<u8>
        - values: string
    - No output

function header_insert(): fastly_status
    - Input:
        - h: response_handle
        - name: mut_slice<u8>
        - value: mut_slice<u8>
    - No output

function header_append(): fastly_status
    - Input:
        - h: response_handle
        - name: mut_slice<u8>
        - value: mut_slice<u8>
    - No output

function header_remove(): fastly_status
    - Input:
        - h: response_handle
        - name: mut_slice<u8>
    - No output

function version_get(): fastly_status
    - Input:
        - h: response_handle
    - Output:
        - mut_ptr<http_version>

function version_set(): fastly_status
    - Input:
        - h: response_handle
        - version: http_version
    - No output

function send_downstream(): fastly_status
    - Input:
        - h: response_handle
        - b: body_handle
        - streaming: u32
    - No output

function status_get(): fastly_status
    - Input:
        - h: response_handle
    - Output:
        - mut_ptr<http_status>

function status_set(): fastly_status
    - Input:
        - h: response_handle
        - status: http_status
    - No output

function close(): fastly_status
    - Input:
        - h: response_handle
    - No output

function framing_headers_mode_set(): fastly_status
    - Input:
        - h: response_handle
        - mode: framing_headers_mode
    - No output

function http_keepalive_mode_set(): fastly_status
    - Input:
        - h: response_handle
        - mode: http_keepalive_mode
    - No output


---------------------- Module: [fastly_kv] ----------------------

alias kv_store_handle = handle

function open(): fastly_status
    - Input:
        - name: string
    - Output:
        - mut_ptr<kv_store_handle>

function lookup(): fastly_status
    - Input:
        - store: kv_store_handle
        - key: mut_slice<u8>
        - opt_body_handle_out: mut_ptr<body_handle>
    - No output

function insert(): fastly_status
    - Input:
        - store: kv_store_handle
        - key: mut_slice<u8>
        - body_handle: body_handle
        - max_age: u32
    - Output:
        - mut_ptr<inserted>


---------------------- Module: [fastly_log] ----------------------

function endpoint_get(): fastly_status
    - Input:
        - name: mut_slice<u8>
    - Output:
        - mut_ptr<endpoint_handle>

function write(): fastly_status
    - Input:
        - h: endpoint_handle
        - msg: mut_slice<u8>
    - Output:
        - mut_ptr<num_bytes>


---------------------- Module: [fastly_object_store] ----------------------

function open(): fastly_status
    - Input:
        - name: string
    - Output:
        - mut_ptr<object_store_handle>

function lookup(): fastly_status
    - Input:
        - store: object_store_handle
        - key: string
        - body_handle_out: mut_ptr<body_handle>
    - No output

function lookup_async(): fastly_status
    - Input:
        - store: object_store_handle
        - key: string
        - pending_handle_out: mut_ptr<pending_object_store_lookup_handle>
    - No output

function pending_lookup_wait(): fastly_status
    - Input:
        - pending_objstr_handle: pending_object_store_lookup_handle
        - body_handle_out: mut_ptr<body_handle>
    - No output

function lookup_as_fd(): fastly_status
    - Input:
        - store: object_store_handle
        - key: string
        - fd_out: mut_ptr<u32>
    - No output

function insert(): fastly_status
    - Input:
        - store: object_store_handle
        - key: string
        - body_handle: body_handle
    - No output

function insert_async(): fastly_status
    - Input:
        - store: object_store_handle
        - key: string
        - body_handle: body_handle
        - pending_handle_out: mut_ptr<pending_object_store_insert_handle>
    - No output

function pending_insert_wait(): fastly_status
    - Input:
        - pending_objstr_handle: pending_object_store_insert_handle
    - No output

function delete_async(): fastly_status
    - Input:
        - store: object_store_handle
        - key: string
        - pending_handle_out: mut_ptr<pending_object_store_delete_handle>
    - No output

function pending_delete_wait(): fastly_status
    - Input:
        - pending_objstr_handle: pending_object_store_delete_handle
    - No output


---------------------- Module: [fastly_purge] ----------------------

function purge_surrogate_key(): fastly_status
    - Input:
        - surrogate_key: string
        - options_mask: purge_options_mask
        - options: mut_ptr<purge_options>
    - No output


---------------------- Module: [fastly_secret_store] ----------------------

function open(): fastly_status
    - Input:
        - name: string
    - Output:
        - mut_ptr<secret_store_handle>

function get(): fastly_status
    - Input:
        - store: secret_store_handle
        - key: string
    - Output:
        - mut_ptr<secret_handle>

function plaintext(): fastly_status
    - Input:
        - secret: secret_handle
        - buf: mut_ptr<char8>
        - buf_len: usize
        - nwritten_out: mut_ptr<usize>
    - No output

function from_bytes(): fastly_status
    - Input:
        - buf: mut_ptr<char8>
        - buf_len: usize
    - Output:
        - mut_ptr<secret_handle>


---------------------- Module: [fastly_uap] ----------------------

function parse(): fastly_status
    - Input:
        - user_agent: string
        - family: mut_ptr<char8>
        - family_len: usize
        - family_nwritten_out: mut_ptr<usize>
        - major: mut_ptr<char8>
        - major_len: usize
        - major_nwritten_out: mut_ptr<usize>
        - minor: mut_ptr<char8>
        - minor_len: usize
        - minor_nwritten_out: mut_ptr<usize>
        - patch: mut_ptr<char8>
        - patch_len: usize
        - patch_nwritten_out: mut_ptr<usize>
    - No output
```

### About `witx`

> The `witx` file format is an experimental format which is based on the
> [module linking] text format (`wit`), (which is in turn based on the
> [wat format], which is based on [S-expressions]). It adds some features
> using the same syntax as [interface types], some features with syntax
> similar to [gc types], as well as a few special features of its own.
>
> The initial goal for `witx` is just to have a language suitable for
> expressing [WASI] APIs in, to serve as the vocabulary for proposing changes
> to existing APIs and proposing new APIs. Initially, while it uses some of
> the syntax and concepts from interface types, it doesn't currently imply the
> full interface types specification, or the use of the interface types custom
> sections.
>
> We expect that eventually we will transition to using the full interface
> types specification, with `witx` having minimal additional features. Until
> then, the goals here are to remain aligned with interface types and other
> relevant WebAssembly standards and proposals wherever practical, and to be an
> input into the design process of interface types.

- [source][witx]

[interface types]: https://github.com/WebAssembly/interface-types/blob/master/proposals/interface-types/Explainer.md
[gc types]: https://github.com/WebAssembly/gc
[module linking]: https://github.com/WebAssembly/module-linking/blob/master/proposals/module-linking/Explainer.md
[S-expressions]: https://en.wikipedia.org/wiki/S-expression
[WASI]: https://github.com/WebAssembly/WASI
[wat format]: https://webassembly.github.io/spec/core/bikeshed/index.html#text-format%E2%91%A0
[witx]: https://github.com/WebAssembly/WASI/blob/main/docs/witx.md
