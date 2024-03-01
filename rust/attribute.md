# `allow(unused_variable)`
```rust
#![allow(unused_variable)]
```
# `allow(dead_code)`
disable the dead_code lint
```rust
#[allow(dead_code)]
unused_function() {}
```

# `crate_type = ""` and `crate_name = ""`
tell the compiler whether a crate is a binary or a library (and even which type 
of library)
the crate_name attribute can be used to set the name of the crate.
```rust
#![crate_type = "lib"]
#![crate_name = "crate_name"]
/* both the crate_type and crate_name attributes have no effect whatsoever when
 * using Cargo, the Rust package manager.  
 */
```

# `cfg` and `cfg!`
