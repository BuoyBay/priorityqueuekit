# Stable min-heaps

Stable min-priority queues, inspired by [Kem Tekinay's heap-based queue](https://github.com/ktekinay/Xojo-PriorityQueue/).
`Import priorityqueuekit` exposes `MinPriorityQueue Of T` with arbitrary statically
known payload types. No native dependencies or Variant boxing.

Equal priorities preserve insertion order, including negative and signed-zero
priorities. Payloads are stored by Buoy's ordinary value/reference semantics;
class references (including Nil) retain their identity. A queued object's fields
can change without affecting its priority. The queue owns its stored references
until removal or Clear. It is synchronous and not thread safe.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add priorityqueuekit --git https://github.com/BuoyBay/priorityqueuekit.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

```basic
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

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer priorityqueuekit
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
