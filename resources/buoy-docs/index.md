---
title: "PriorityQueueKit"
summary: "Schedule statically typed payloads with a stable bounded min-priority heap."
category: "Overview"
order: 0
keywords: ["queue", "priority", "heap", "stable", "generic"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# PriorityQueueKit

PriorityQueueKit exposes `MinPriorityQueue Of T`, a pure Buoy stable min-priority queue for arbitrary statically known payload types. Lower Double priorities are removed first. Equal priorities preserve insertion order, including negative and signed-zero priorities.

## Payload and ordering model

The queue stores payloads using normal Buoy value/reference semantics. Class references, including Nil, retain identity. Changing a queued object's fields does not change its stored priority. Stored references remain owned by the queue until removal, Clear, or destruction.

`Add` and `Pop` use O(log n) heap operations. Peek is O(1), storage O(n). A configured entry-count limit prevents unbounded registration, but it is not a byte-memory quota. Underlying arrays can retain backing allocation after removals or Clear.

## Scope and failures

The package supports min-first ordering only. It has no priority-update/remove-by-handle API, custom comparator, max-first mode, serialization, or concurrent queue. It is synchronous and not thread safe.

Empty reads/removals, invalid capacities, nonfinite priorities, capacity exhaustion, and insertion-sequence exhaustion throw `InvalidArgumentException` before mutation. Clear releases payload references and resets insertion ordering.

Read [Getting started](getting-started.md) for stable job ordering, or [API reference](api.md) for the exact capacity and lifetime contracts.
