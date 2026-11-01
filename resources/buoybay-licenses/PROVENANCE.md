# Source study

Source: https://github.com/ktekinay/Xojo-PriorityQueue/

Inspected master commit `8dd76b9bd5a6741379d3edbd00202a521cc20493`, README,
`PriorityQueue_MTC.xojo_code`, tests and MIT license. Upstream uses parallel arrays
and a binary heap for Double priorities and Variant payloads, supports ascending
and descending queues, exposes Add/Pop/PeekPriority/PeekValue/Count/Clear, and
returns NaN for an empty PeekPriority. Its source is Copyright 2023 Kem Tekinay;
the complete notice is retained in UPSTREAM-LICENSE.txt.

This package is an independent Buoy implementation of the generic heap technique,
with explicit stable insertion ordering and bounds; no Xojo source or harness was
transcribed. The installed Buoy 0.72.0 standard-library index has generic arrays,
sorting and maps but no dedicated heap/priority queue API. Sorting an array after
every insert works but costs more than a heap for repeated dequeue workloads.

Parity differences: min-first only; strongly typed generic payloads rather than
Variant; stable equal-priority ties guaranteed; finite priorities only; empty
operations throw; capacity and sequence exhaustion reject explicitly; no upstream
allocation-growth/shrink policy or performance claims are inherited.
