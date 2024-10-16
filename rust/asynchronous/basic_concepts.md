# Non-preemptive multitasking (cooperative multitasking)
The first method used to be able to keep a UI interative (and running 
background processes).
> by programmer

# Preemptive multitasking
> by the os

# Hyper-threading
ALUs(arithmetic logic units)
When an operation only required some parts of the CPU, an instruction could be 
run on the ALU simultaneously. This is become the start of hyper-threading.

# naked functions
A naked functions tells the compiler that we don't want it to create a function
prologue (序) and epilogue and that we want to take care of this ourselves.
```rust
#![feature(naked_functions)]
```
