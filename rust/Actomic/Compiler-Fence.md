# Compiler Fence
> std::sync::atomic::compiler_fence

It effects are restricted to just the compiler.

It does not prevent the processor from.

# Use cases
- implement a Unix signal handler
- an interrupt on embedded system
- process-wide memory barriers
