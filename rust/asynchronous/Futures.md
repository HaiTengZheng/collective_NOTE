# future
A future is a representation of some operation that will be completed in the 
future

# Async in Rust uses a poll-based approach
three phases
1. the poll phase
- often refer to the part of the runtime that polls a future as an `executor`
2. the wait phase
- an event source, most often refferred to as a reactor
3. the wake phase

# leaf futures
Runtimes create leaf futures, which represent a resource such as a socket

# non-leaf futures
Non-leaf futures are the kind of futures we as users of a runtime write
ourselves using the async keyword to create a task can be run on the executor
