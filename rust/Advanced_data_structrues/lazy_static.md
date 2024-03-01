# lazy_static!
```toml
lazy_static = "1.0"
```
The `lazy_static!` macro helps with this by extending Rust's normal `static`
functionality, which normally requires your objects to be constructable at 
compile-time, with the ability to create lazy objects that are initialized 
during runtime
