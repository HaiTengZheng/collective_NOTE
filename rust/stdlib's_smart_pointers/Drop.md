# Drop trait
related to resource management and automatic cleanup when a value goes out of 
scope
- provide a way to run custom code when a value is about to go out of scope,
  allowing you to clean up resource associated with the value.
```rust
pub trait Drop {
    fn drop(&mut self);
}
```
