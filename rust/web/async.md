# concepts
## concurrency
> executing parts of a program out of order

## parallelism
> executing multiple tasks sumultaneously

## two models of the concurrency processing
- multithreading        (Rust standard library: std::thread)
- async processing

## threading models
- 1:1 thread model      (a single operating system thread per language thread)
- M:N model             (M green(quasi) threads per N operating system threads)

The Rust standard library implements the 1:1 thread model, but does not mean
    that we can create an endless number of threads corresponding to new
    network requests.

Each operating system has a limit on the number of threads, and this is also
    influenced by the stack size and amount of virtual memory available in the
    server.

# processing catefories
- CPU-intensive tasks
- I/O-intensive tasks

