<!--- Hugo front matter used to generate the website version of this page:
linkTitle: V8 JS engine
--->

# Semantic Conventions for V8 JS Engine Runtime Metrics

**Status**: [Experimental][DocumentStatus]

This document describes semantic conventions for V8 JS Engine Runtime metrics in OpenTelemetry. This engine is used in some javascript runtime such as Node.js and Deno.

<!-- Re-generate TOC with `markdown-toc --no-first-h1 -i` -->

<!-- toc -->

- [Experimental](#experimental)
  - [Metric: `v8js.gc.duration`](#metric-v8jsgcduration)
  - [Metric: `v8js.memory.heap.limit`](#metric-v8jsmemoryheaplimit)
  - [Metric: `v8js.memory.heap.used`](#metric-v8jsmemoryheapused)
  - [Metric: `v8js.heap.space.available_size`](#metric-v8jsheapspaceavailable_size)
  - [Metric: `v8js.heap.space.physical_size`](#metric-v8jsheapspacephysical_size)

<!-- tocstop -->

## Experimental

**Status**: [Experimental][DocumentStatus]

**Description:** Experimental V8 JS Engine Runtime metrics captured under `v8js`.

### Metric: `v8js.gc.duration`

This metric is [recommended][MetricRecommended].

This metric SHOULD be specified with
[`ExplicitBucketBoundaries`](https://github.com/open-telemetry/opentelemetry-specification/tree/v1.41.0/specification/metrics/api.md#instrument-advisory-parameters)
of `[ 0.01, 0.1, 1, 10 ]`.

<!-- semconv metric.v8js.gc.duration -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `v8js.gc.duration` | Histogram | `s` | Garbage collection duration. [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** The values can be retrieve from [`perf_hooks.PerformanceObserver(...).observe({ entryTypes: ['gc'] })`](https://nodejs.org/api/perf_hooks.html#performanceobserverobserveoptions)

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`v8js.gc.type`](/docs/attributes-registry/v8js.md) | string | The type of garbage collection. | `major`; `minor`; `incremental` | `Required` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

---

`v8js.gc.type` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `incremental` | Incremental (Incremental Marking). | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `major` | Major (Mark Sweep Compact). | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `minor` | Minor (Scavenge). | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `weakcb` | Weak Callbacks (Process Weak Callbacks). | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `v8js.memory.heap.limit`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.v8js.memory.heap.limit -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `v8js.memory.heap.limit` | UpDownCounter | `By` | Total heap memory size pre-allocated. [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** The value can be retrieved from value `space_size` of [`v8.getHeapSpaceStatistics()`](https://nodejs.org/api/v8.html#v8getheapspacestatistics)

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`v8js.heap.space.name`](/docs/attributes-registry/v8js.md) | string | The name of the space type of heap memory. [1] | `new_space`; `old_space`; `code_space` | `Required` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `v8js.heap.space.name`:** Value can be retrieved from value `space_name` of [`v8.getHeapSpaceStatistics()`](https://nodejs.org/api/v8.html#v8getheapspacestatistics)

---

`v8js.heap.space.name` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `code_space` | Code memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `large_object_space` | Large object memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `map_space` | Map memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `new_space` | New memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `old_space` | Old memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `v8js.memory.heap.used`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.v8js.memory.heap.used -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `v8js.memory.heap.used` | UpDownCounter | `By` | Heap Memory size allocated. [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** The value can be retrieved from value `space_used_size` of [`v8.getHeapSpaceStatistics()`](https://nodejs.org/api/v8.html#v8getheapspacestatistics)

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`v8js.heap.space.name`](/docs/attributes-registry/v8js.md) | string | The name of the space type of heap memory. [1] | `new_space`; `old_space`; `code_space` | `Required` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `v8js.heap.space.name`:** Value can be retrieved from value `space_name` of [`v8.getHeapSpaceStatistics()`](https://nodejs.org/api/v8.html#v8getheapspacestatistics)

---

`v8js.heap.space.name` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `code_space` | Code memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `large_object_space` | Large object memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `map_space` | Map memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `new_space` | New memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `old_space` | Old memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `v8js.heap.space.available_size`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.v8js.heap.space.available_size -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `v8js.heap.space.available_size` | UpDownCounter | `By` | Heap space available size. [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** Value can be retrieved from value `space_available_size` of [`v8.getHeapSpaceStatistics()`](https://nodejs.org/api/v8.html#v8getheapspacestatistics)

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`v8js.heap.space.name`](/docs/attributes-registry/v8js.md) | string | The name of the space type of heap memory. [1] | `new_space`; `old_space`; `code_space` | `Required` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `v8js.heap.space.name`:** Value can be retrieved from value `space_name` of [`v8.getHeapSpaceStatistics()`](https://nodejs.org/api/v8.html#v8getheapspacestatistics)

---

`v8js.heap.space.name` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `code_space` | Code memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `large_object_space` | Large object memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `map_space` | Map memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `new_space` | New memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `old_space` | Old memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

### Metric: `v8js.heap.space.physical_size`

This metric is [recommended][MetricRecommended].

<!-- semconv metric.v8js.heap.space.physical_size -->
<!-- NOTE: THIS TEXT IS AUTOGENERATED. DO NOT EDIT BY HAND. -->
<!-- see templates/registry/markdown/snippet.md.j2 -->
<!-- prettier-ignore-start -->
<!-- markdownlint-capture -->
<!-- markdownlint-disable -->

| Name     | Instrument Type | Unit (UCUM) | Description    | Stability |
| -------- | --------------- | ----------- | -------------- | --------- |
| `v8js.heap.space.physical_size` | UpDownCounter | `By` | Committed size of a heap space. [1] | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1]:** Value can be retrieved from value `physical_space_size` of [`v8.getHeapSpaceStatistics()`](https://nodejs.org/api/v8.html#v8getheapspacestatistics)

| Attribute  | Type | Description  | Examples  | [Requirement Level](https://opentelemetry.io/docs/specs/semconv/general/attribute-requirement-level/) | Stability |
|---|---|---|---|---|---|
| [`v8js.heap.space.name`](/docs/attributes-registry/v8js.md) | string | The name of the space type of heap memory. [1] | `new_space`; `old_space`; `code_space` | `Required` | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

**[1] `v8js.heap.space.name`:** Value can be retrieved from value `space_name` of [`v8.getHeapSpaceStatistics()`](https://nodejs.org/api/v8.html#v8getheapspacestatistics)

---

`v8js.heap.space.name` has the following list of well-known values. If one of them applies, then the respective value MUST be used; otherwise, a custom value MAY be used.

| Value  | Description | Stability |
|---|---|---|
| `code_space` | Code memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `large_object_space` | Large object memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `map_space` | Map memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `new_space` | New memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |
| `old_space` | Old memory space. | ![Experimental](https://img.shields.io/badge/-experimental-blue) |

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->
<!-- END AUTOGENERATED TEXT -->
<!-- endsemconv -->

[DocumentStatus]: https://github.com/open-telemetry/opentelemetry-specification/tree/v1.41.0/specification/document-status.md
[MetricRecommended]: /docs/general/metric-requirement-level.md#recommended
