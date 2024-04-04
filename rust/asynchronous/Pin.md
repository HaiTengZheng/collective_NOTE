# Pin
a struct
```rust
#[repr(transparent)]
pub struct Pin<P> { /* private fields */ }
```

# Unpin
a trait
```rust
pub auto trait Unpin { }
```
即使类型实现了 Unpin 其依然可以 Pin 然而不会有任何效果，该值一样可以被移动。
`Pin<&mut u8>` is equal to `&mut u8`
