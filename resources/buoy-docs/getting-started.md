---
title: "PriorityQueueKit getting started"
summary: "Insert jobs with explicit priorities and remove tied jobs in registration order."
category: "Guides"
order: 10
keywords: ["jobs", "stable", "min", "pop", "peek"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

Install `priorityqueuekit` through BPM or put `priorityqueuekit-0.1.0.buipkg` in the consumer's `packages/`. Use `Import priorityqueuekit`. No native dependencies are required.

## Process the most urgent jobs first

This complete console example enqueues one background job and two tied urgent jobs. The first urgent job is removed before the second because ties preserve insertion order.

```buoy
Import priorityqueuekit

Sub Main()
    Dim jobs As New MinPriorityQueue Of String(100)
    jobs.Add(10.0, "background refresh")
    jobs.Add(1.0, "first urgent job")
    jobs.Add(1.0, "second urgent job")
    While jobs.Count > 0
        Print String.From(jobs.PeekPriority()) + ": " + jobs.Pop()
    End While
End Sub
```

Lower values have higher removal priority. A negative priority is valid. Use explicit Double priorities, as shown, rather than relying on arithmetic promotion when calculating fractional priorities from Integer values.

## Choose a capacity and owner

The constructor's limit is the maximum number of queued entries, not initial preallocated storage or a byte budget. Size it for your workload and check Count when deciding whether to accept additional work. Invalid inserts throw without changing existing queue contents.

Retain the queue on one thread. A queued class payload remains a reference to the original object; update it only under your application's ownership rules. If you need to change a priority, the package provides no update handle—design a separate host-level scheduling policy rather than mutating internal heap state.

Use `Clear()` to discard all queued payload references and reset the insertion-order counter. Guard Peek/Pop with Count, or handle the empty-queue exception at your application boundary.

Continue with [API reference](api.md), or return to [PriorityQueueKit](index.md).
