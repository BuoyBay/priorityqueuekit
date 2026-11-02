# PriorityQueueKit 0.1.0

Pure Buoy stable min-priority queues, inspired by [Kem Tekinay's heap-based queue](https://github.com/ktekinay/Xojo-PriorityQueue/).
`Import priorityqueuekit` exposes `MinPriorityQueue Of T` with arbitrary statically
known payload types. No native dependencies or Variant boxing.

- `New MinPriorityQueue Of T(maxEntries = 100000)` accepts capacities 1..1000000.
- `Add(priority As Double, value As T)` inserts a finite priority and payload.
- `PeekPriority()`, `PeekValue()` inspect the minimum without removing it.
- `Pop()` removes and returns the payload with the lowest priority.
- `Count`, `Capacity` are read-only properties; `Clear()` releases payloads and resets insertion ordering.

Equal priorities preserve insertion order, including negative and signed-zero
priorities. Payloads are stored by Buoy's ordinary value/reference semantics;
class references (including Nil) retain their identity. A queued object's fields
can change without affecting its priority. The queue owns its stored references
until removal or Clear. It is synchronous and not thread safe.

Empty reads/removals, invalid capacities, nonfinite priorities and full capacity
throw `InvalidArgumentException` before mutating the queue. Sequence exhaustion
also rejects inserts; Clear resets it. The capacity is an entry-count ceiling,
not a byte-memory quota. Add/Pop are O(log n), peek is O(1), and storage is O(n).
The arrays may retain backing allocation after removals or Clear.

This independent implementation covers min-first queues only. Unlike upstream,
it adds stable ties, static generic payloads and explicit entry limits, and uses
exceptions instead of upstream's NaN sentinel for an empty PeekPriority. There is
no priority-update/remove-by-handle API, custom comparator, max-first mode,
serialization, or concurrent queue. See [provenance](../PROVENANCE.md).
