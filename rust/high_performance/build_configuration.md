# [profile.{profile}] foromat in Cargo.toml
- dev           `cargo build` or `cargo run`
- release       `cargo build --release` or `cargo run --release`
- test          `cargo test`
- bench         `cargo bench`
- doc           `cargo doc`

# optimization level
```toml
[profile.release]
opt-level = 2
```

# debug information
```toml
[profile.test]
debug = free
```
Debug symbols will also show information about the original code, so it might 
make sense to hide it in closed-source projects.

# link-time optimization (LTO)
It's not enabled by default in any of the profiles.
```toml
[profile.release]
lto = true
```
## the `codegen` units
This divides the codes into multiple smaller code units and compiles each of them
separately, enabling parallel compiling.
```toml
[profile.dev]
codegen-units = 32
```
Do not use it in the release profile.

# debug assertions
By default, they are noly executed in the development profile.
They are written in the code by prefixing the `assert!` macros with `debug_`,
e.g, `debug_assert!` and `debug_assert_eq!`.
```toml
[profile.doc]
debug_assertion = false
```

# panic behavior
By default, Rust will unwind in a panic.
```toml
[profile.doc]
panic = 'abort'
```

# runtime library paths
rpath
> cargo -C rpath
