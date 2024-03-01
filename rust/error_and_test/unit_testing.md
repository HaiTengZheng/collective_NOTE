# Unit testing
```rust
#[cfg(tests)] // tells the compiler this is uor unit test mod
mod tests {   //
    use super::*;

    #[test] // tells the compiler this function 
}
```

# test framework
- the parameterized crate
- the test-case crate
- the retest crate
- the assert2

# Arithmetic overflow in Rust
In Rust, code compiled in debug mode (such as tests) use checked arithmetic by 
default. When the same code is compiled in release mode, the same code will be 
use unchecked arithmetic.
## emulate C behaviour (RFC 560)
the `Wrapping` struct

