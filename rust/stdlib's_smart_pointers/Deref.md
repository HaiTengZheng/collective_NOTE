# Deref trait
```rust
trait Deref<T> {
    type Target: ?Sized;

    fn deref(&self) -> &Target;
}
```

# deref()

