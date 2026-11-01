# Priority queue study

See [PriorityQueueKit](../../../libraries/priorityqueuekit/README.md) for the API,
source study, intentional differences and package usage.

Run `python3 tests/xos_priorityqueue_verify.py` from the repository root. It seals
a fresh package, checks the module/test/example for six targets, and executes the
example and behavioral tests on the host. The example demonstrates stable urgent
job ordering without starting threads, opening a UI or running submitted jobs.
