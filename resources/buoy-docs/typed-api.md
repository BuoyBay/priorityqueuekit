---
title: "priorityqueuekit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["MinPriorityQueue"]
dependencies: []
symbols: ["MinPriorityQueue"]
related: ["api.md", "getting-started.md", "index.md"]
---

# priorityqueuekit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## MinPriorityQueue

`Public Class MinPriorityQueue Of T`

Stable min-priority binary heap. Equal priorities preserve insertion order.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Count` | `Integer` | Yes | No | — | — |
| `Capacity` | `Integer` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(maxEntries As Integer = 100000)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `maxEntries` | `Integer` | `ByVal` | `100000` |

Returns: no value.

### Add

`Public Sub Add(priority As Double, value As T)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `priority` | `Double` | `ByVal` | Required |
| `value` | `T` | `ByVal` | Required |

Returns: no value.

### PeekValue

`Public Function PeekValue() As T`

No parameters.

#### Returns

| Type |
| --- |
| `T` |

### PeekPriority

`Public Function PeekPriority() As Double`

No parameters.

#### Returns

| Type |
| --- |
| `Double` |

### Pop

`Public Function Pop() As T`

No parameters.

#### Returns

| Type |
| --- |
| `T` |

### Clear

`Public Sub Clear()`

No parameters.

Returns: no value.
