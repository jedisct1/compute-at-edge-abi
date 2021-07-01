# Fastly Compute@Edge ABI

This repository contains `witx` definitions for the Compute@Edge platform ABI.

This fork includes definitions that have been [updated](https://github.com/jedisct1/compute-at-edge-abi/tree/witx-next/witx-next)
to be compatible with the [witx-codegen](https://github.com/jedisct1/witx-codegen) code generator.

### [Documentation](https://github.com/jedisct1/compute-at-edge-abi/tree/witx-next/doc)

* [fastly_abi](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_abi.witx.md)
* [fastly_dictionary](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_dictionary.witx.md)
* [fastly_geo](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_geo.witx.md)
* [fastly_http_body](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_http_body.witx.md)
* [fastly_http_req](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_http_req.witx.md)
* [fastly_http_resp](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_http_resp.witx.md)
* [fastly_log](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_log.witx.md)
* [fastly_uap](https://github.com/jedisct1/compute-at-edge-abi/blob/witx-next/doc/fastly_uap.witx.md)

### API overview

```text
---------------------- Module: [typenames] ----------------------

enum fastly_status: (tag: u32)
    - `ok`: fastly_status
    - `error`: fastly_status
    - `inval`: fastly_status
    - `badf`: fastly_status
    - `buflen`: fastly_status
    - `unsupported`: fastly_status
    - `badalign`: fastly_status
    - `httpinvalid`: fastly_status
    - `httpuser`: fastly_status
    - `httpincomplete`: fastly_status
    - `none`: fastly_status
    - `httpheadtoolarge`: fastly_status
    - `httpinvalidstatus`: fastly_status

enum http_version: (tag: u32)
    - `http_09`: http_version
    - `http_10`: http_version
    - `http_11`: http_version
    - `h2`: http_version
    - `h3`: http_version

alias http_status = u16

enum body_write_end: (tag: u32)
    - `back`: body_write_end
    - `front`: body_write_end

alias body_handle = handle

alias request_handle = handle

alias response_handle = handle

alias pending_request_handle = handle

alias endpoint_handle = handle

alias dictionary_handle = handle

alias multi_value_cursor = u32

alias multi_value_cursor_result = i64

constants cache_override_tag: (type: u32)
predefined constants for cache_override_tag:
    - `none` = 0x1
    - `pass` = 0x2
    - `ttl` = 0x4
    - `stale_while_revalidate` = 0x8
    - `pci` = 0x10

alias num_bytes = usize

alias header_count = u32

alias is_done = u32

alias done_idx = u32


---------------------- Module: [fastly_abi] ----------------------

enum fastly_status: (tag: u32)
    - `ok`: fastly_status
    - `error`: fastly_status
    - `inval`: fastly_status
    - `badf`: fastly_status
    - `buflen`: fastly_status
    - `unsupported`: fastly_status
    - `badalign`: fastly_status
    - `httpinvalid`: fastly_status
    - `httpuser`: fastly_status
    - `httpincomplete`: fastly_status
    - `none`: fastly_status
    - `httpheadtoolarge`: fastly_status
    - `httpinvalidstatus`: fastly_status

enum http_version: (tag: u32)
    - `http_09`: http_version
    - `http_10`: http_version
    - `http_11`: http_version
    - `h2`: http_version
    - `h3`: http_version

alias http_status = u16

enum body_write_end: (tag: u32)
    - `back`: body_write_end
    - `front`: body_write_end

alias body_handle = handle

alias request_handle = handle

alias response_handle = handle

alias pending_request_handle = handle

alias endpoint_handle = handle

alias dictionary_handle = handle

alias multi_value_cursor = u32

alias multi_value_cursor_result = i64

constants cache_override_tag: (type: u32)
predefined constants for cache_override_tag:
    - `none` = 0x1
    - `pass` = 0x2
    - `ttl` = 0x4
    - `stale_while_revalidate` = 0x8
    - `pci` = 0x10

alias num_bytes = usize

alias header_count = u32

alias is_done = u32

alias done_idx = u32

function init(): fastly_status
    - Input:
        - `abi_version`: u64
    - No output


---------------------- Module: [fastly_dictionary] ----------------------

function open(): fastly_status
    - Input:
        - `name`: string
    - Output:
        - mut_ptr<dictionary_handle>

function get(): fastly_status
    - Input:
        - `h`: dictionary_handle
        - `key`: string
        - `value`: mut_ptr<char8>
        - `value_max_len`: usize
    - Output:
        - mut_ptr<num_bytes>


---------------------- Module: [fastly_geo] ----------------------

function lookup(): fastly_status
    - Input:
        - `addr_octets`: ptr<char8>
        - `addr_len`: usize
        - `buf`: mut_ptr<char8>
        - `buf_len`: usize
        - `nwritten_out`: mut_ptr<usize>
    - No output


---------------------- Module: [fastly_http_body] ----------------------

function append(): fastly_status
    - Input:
        - `dest`: body_handle
        - `src`: body_handle
    - No output

function new(): fastly_status
    - Output:
        - mut_ptr<body_handle>

function read(): fastly_status
    - Input:
        - `h`: body_handle
        - `buf`: mut_ptr<u8>
        - `buf_len`: usize
    - Output:
        - mut_ptr<num_bytes>

function write(): fastly_status
    - Input:
        - `h`: body_handle
        - `buf`: mut_slice<u8>
        - `end`: body_write_end
    - Output:
        - mut_ptr<num_bytes>

function close(): fastly_status
    - Input:
        - `h`: body_handle
    - No output


---------------------- Module: [fastly_http_req] ----------------------

function body_downstream_get(): fastly_status
    - Output:
        - mut_ptr<request_handle>
        - mut_ptr<body_handle>

function cache_override_set(): fastly_status
    - Input:
        - `h`: request_handle
        - `tag`: cache_override_tag
        - `ttl`: u32
        - `stale_while_revalidate`: u32
    - No output

function cache_override_v2_set(): fastly_status
    - Input:
        - `h`: request_handle
        - `tag`: cache_override_tag
        - `ttl`: u32
        - `stale_while_revalidate`: u32
        - `sk`: mut_slice<u8>
    - No output

function downstream_client_ip_addr(): fastly_status
    - Input:
        - `addr_octets_out`: mut_ptr<char8>
    - Output:
        - mut_ptr<num_bytes>

function downstream_tls_cipher_openssl_name(): fastly_status
    - Input:
        - `cipher_out`: mut_ptr<char8>
        - `cipher_max_len`: usize
        - `nwritten_out`: mut_ptr<usize>
    - No output

function downstream_tls_protocol(): fastly_status
    - Input:
        - `protocol_out`: mut_ptr<char8>
        - `protocol_max_len`: usize
        - `nwritten_out`: mut_ptr<usize>
    - No output

function downstream_tls_client_hello(): fastly_status
    - Input:
        - `chello_out`: mut_ptr<char8>
        - `chello_max_len`: usize
        - `nwritten_out`: mut_ptr<usize>
    - No output

function new(): fastly_status
    - Output:
        - mut_ptr<request_handle>

function header_names_get(): fastly_status
    - Input:
        - `h`: request_handle
        - `buf`: mut_ptr<char8>
        - `buf_len`: usize
        - `cursor`: multi_value_cursor
        - `ending_cursor_out`: mut_ptr<multi_value_cursor_result>
        - `nwritten_out`: mut_ptr<usize>
    - No output

function original_header_names_get(): fastly_status
    - Input:
        - `buf`: mut_ptr<char8>
        - `buf_len`: usize
        - `cursor`: multi_value_cursor
        - `ending_cursor_out`: mut_ptr<multi_value_cursor_result>
        - `nwritten_out`: mut_ptr<usize>
    - No output

function original_header_count(): fastly_status
    - Output:
        - mut_ptr<header_count>

function header_value_get(): fastly_status
    - Input:
        - `h`: request_handle
        - `name`: mut_slice<u8>
        - `value`: mut_ptr<char8>
        - `value_max_len`: usize
        - `nwritten_out`: mut_ptr<usize>
    - No output

function header_values_get(): fastly_status
    - Input:
        - `h`: request_handle
        - `name`: mut_slice<u8>
        - `buf`: mut_ptr<char8>
        - `buf_len`: usize
        - `cursor`: multi_value_cursor
        - `ending_cursor_out`: mut_ptr<multi_value_cursor_result>
        - `nwritten_out`: mut_ptr<usize>
    - No output

function header_values_set(): fastly_status
    - Input:
        - `h`: request_handle
        - `name`: mut_slice<u8>
        - `values`: string
    - No output

function header_insert(): fastly_status
    - Input:
        - `h`: request_handle
        - `name`: mut_slice<u8>
        - `value`: mut_slice<u8>
    - No output

function header_append(): fastly_status
    - Input:
        - `h`: request_handle
        - `name`: mut_slice<u8>
        - `value`: mut_slice<u8>
    - No output

function header_remove(): fastly_status
    - Input:
        - `h`: request_handle
        - `name`: mut_slice<u8>
    - No output

function method_get(): fastly_status
    - Input:
        - `h`: request_handle
        - `buf`: mut_ptr<char8>
        - `buf_len`: usize
        - `nwritten_out`: mut_ptr<usize>
    - No output

function method_set(): fastly_status
    - Input:
        - `h`: request_handle
        - `method`: string
    - No output

function uri_get(): fastly_status
    - Input:
        - `h`: request_handle
        - `buf`: mut_ptr<char8>
        - `buf_len`: usize
        - `nwritten_out`: mut_ptr<usize>
    - No output

function uri_set(): fastly_status
    - Input:
        - `h`: request_handle
        - `uri`: string
    - No output

function version_get(): fastly_status
    - Input:
        - `h`: request_handle
    - Output:
        - mut_ptr<http_version>

function version_set(): fastly_status
    - Input:
        - `h`: request_handle
        - `version`: http_version
    - No output

function send(): fastly_status
    - Input:
        - `h`: request_handle
        - `b`: body_handle
        - `backend`: string
    - Output:
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function send_async(): fastly_status
    - Input:
        - `h`: request_handle
        - `b`: body_handle
        - `backend`: string
    - Output:
        - mut_ptr<pending_request_handle>

function send_async_streaming(): fastly_status
    - Input:
        - `h`: request_handle
        - `b`: body_handle
        - `backend`: string
    - Output:
        - mut_ptr<pending_request_handle>

function pending_req_poll(): fastly_status
    - Input:
        - `h`: pending_request_handle
    - Output:
        - mut_ptr<is_done>
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function pending_req_wait(): fastly_status
    - Input:
        - `h`: pending_request_handle
    - Output:
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>

function pending_req_select(): fastly_status
    - Input:
        - `hs`: mut_slice<pending_request_handle>
    - Output:
        - mut_ptr<done_idx>
        - mut_ptr<response_handle>
        - mut_ptr<body_handle>


---------------------- Module: [fastly_http_resp] ----------------------

function new(): fastly_status
    - Output:
        - mut_ptr<response_handle>

function header_names_get(): fastly_status
    - Input:
        - `h`: response_handle
        - `buf`: mut_ptr<char8>
        - `buf_len`: usize
        - `cursor`: multi_value_cursor
        - `ending_cursor_out`: mut_ptr<multi_value_cursor_result>
        - `nwritten_out`: mut_ptr<usize>
    - No output

function header_value_get(): fastly_status
    - Input:
        - `h`: response_handle
        - `name`: mut_slice<u8>
        - `value`: mut_ptr<char8>
        - `value_max_len`: usize
        - `nwritten_out`: mut_ptr<usize>
    - No output

function header_values_get(): fastly_status
    - Input:
        - `h`: response_handle
        - `name`: mut_slice<u8>
        - `buf`: mut_ptr<char8>
        - `buf_len`: usize
        - `cursor`: multi_value_cursor
        - `ending_cursor_out`: mut_ptr<multi_value_cursor_result>
        - `nwritten_out`: mut_ptr<usize>
    - No output

function header_values_set(): fastly_status
    - Input:
        - `h`: response_handle
        - `name`: mut_slice<u8>
        - `values`: string
    - No output

function header_insert(): fastly_status
    - Input:
        - `h`: response_handle
        - `name`: mut_slice<u8>
        - `value`: mut_slice<u8>
    - No output

function header_append(): fastly_status
    - Input:
        - `h`: response_handle
        - `name`: mut_slice<u8>
        - `value`: mut_slice<u8>
    - No output

function header_remove(): fastly_status
    - Input:
        - `h`: response_handle
        - `name`: mut_slice<u8>
    - No output

function version_get(): fastly_status
    - Input:
        - `h`: response_handle
    - Output:
        - mut_ptr<http_version>

function version_set(): fastly_status
    - Input:
        - `h`: response_handle
        - `version`: http_version
    - No output

function send_downstream(): fastly_status
    - Input:
        - `h`: response_handle
        - `b`: body_handle
        - `streaming`: u32
    - No output

function status_get(): fastly_status
    - Input:
        - `h`: response_handle
    - Output:
        - mut_ptr<http_status>

function status_set(): fastly_status
    - Input:
        - `h`: response_handle
        - `status`: http_status
    - No output


---------------------- Module: [fastly_log] ----------------------

function endpoint_get(): fastly_status
    - Input:
        - `name`: mut_slice<u8>
    - Output:
        - mut_ptr<endpoint_handle>

function write(): fastly_status
    - Input:
        - `h`: endpoint_handle
        - `msg`: mut_slice<u8>
    - Output:
        - mut_ptr<num_bytes>


---------------------- Module: [fastly_uap] ----------------------

function parse(): fastly_status
    - Input:
        - `user_agent`: string
        - `family`: mut_ptr<char8>
        - `family_len`: usize
        - `family_nwritten_out`: mut_ptr<usize>
        - `major`: mut_ptr<char8>
        - `major_len`: usize
        - `major_nwritten_out`: mut_ptr<usize>
        - `minor`: mut_ptr<char8>
        - `minor_len`: usize
        - `minor_nwritten_out`: mut_ptr<usize>
        - `patch`: mut_ptr<char8>
        - `patch_len`: usize
        - `patch_nwritten_out`: mut_ptr<usize>
    - No output
```

### About `witx`

> The `witx` file format is an experimental format which is based on the
> [module linking] text format (`wit`), (which is in turn based on the
> [wat format], which is based on [S-expressions]). It adds some features
> using the same syntax as [interface types], some features with syntax
> similar to [gc types], as well as a few special features of its own.
>
> `witx` is actively evolving. Expect backwards-incompatible changes,
> particularly in the areas where `witx` differs from `wit`.
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
