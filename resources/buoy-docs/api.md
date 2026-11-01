---
title: "PriorityQueueKit API"
summary: "Generic stable min-queue construction, insertion, peeking, removal, and cleanup."
category: "Reference"
order: 20
keywords: ["MinPriorityQueue", "capacity", "priority", "sequence", "clear"]
symbols: ["MinPriorityQueue", "MinPriorityQueue.Add", "MinPriorityQueue.Pop", "MinPriorityQueue.PeekValue", "MinPriorityQueue.PeekPriority", "MinPriorityQueue.Count", "MinPriorityQueue.Capacity", "MinPriorityQueue.Clear"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# API reference

## Queue operations

| Member | Contract |
| --- | --- |
| `New MinPriorityQueue Of T(maxEntries = 100000)` | Entry capacity must be 1 through 1,000,000 |
| `Add(priority As Double, value As T)` | Insert finite priority and payload; equal priorities retain insertion order |
| `PeekValue()` | Inspect the minimum payload without removing it |
| `PeekPriority()` | Inspect the minimum stored Double priority |
| `Pop()` | Remove and return the minimum payload |
| `Count` | Read-only current entry count |
| `Capacity` | Read-only configured entry ceiling |
| `Clear()` | Release all payload references, remove entries, reset insertion sequence |

Ordering compares priorities first and insertion sequence second. Negative priorities and signed zero are supported. Add/Pop are O(log n), Peek O(1), and storage O(n). Payload types are static generics rather than Variant boxes.

## Exceptions and lifetime

`InvalidArgumentException` rejects invalid capacity, NaN/infinite priority, insertion at capacity, exhausted insertion sequence, and empty Peek/Pop operations. Validation happens before a rejected insertion mutates the queue. Clear permits a new insertion sequence after exhaustion.

Normal value/reference semantics apply to payloads. Class instances retain identity, Nil class payloads are permitted, and object-field changes do not alter priority. The queue owns references while queued. Backing array allocation may remain after entries are removed or cleared.

The queue performs no locking or thread dispatch. It does not expose arbitrary deletion, priority updates, comparators, max-priority mode, persistence, or a concurrent producer/consumer protocol.

See [Getting started](getting-started.md) and the [overview](index.md).


[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
