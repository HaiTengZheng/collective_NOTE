# Enum: `Ordering`
> std::sync::atomic::Ordering;
```rust
// The `non_exhaustive` attribute indicates that a type or variant may have more 
// fields or variants added in the future. 
// It can be applied to structs, enums, and enum variants.
#[non_exhaustive]
pub enum Ordering {
    Relaxed,    // weakest
    Release,    // applies to store operations
    Acquire,    // applies to load operations
    AcqRel,     // used to represent the combination of `Acquire` and `Release`
    SeqCst,     // Sequentially consistent ordering
}
```

# Relaxed
No ordering constraints, only atomic operations.

# Release and Acquire
`Release` and `Acquire` memory ordering are used **in a pair** to form a
happens-before relationship between threads.

# AcqRel

# SeqCst
The strongest memory ordering. It includes all the guarantees of acquire ordering
(for loads) and release ordering (for stores), and also guarantees a globally
consistent order of operations.

# Consume Ordering
A lightweight --- more efficient --- vaariant of acquire ordering, whose
synchronizing effects are limited to things that depend on the loaded value.

# The total modification order
The ordered list of all modification that happen to an atomic variable.
