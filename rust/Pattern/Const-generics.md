# Const Generics
Rust's `const generics` are a neat twist on generics that allow you to use 
constant values generically.

We can use `const generics` anywhere we have both a primitive constant and a 
generic parameter.

```rust
#[derive(Debug)]
struct Buffer<T, const LENGTH: usize> {
    buf: [T; LENGTH],
}

// generic From 
impl<T, const LENGTH: usize> From<[T; LENGTH]> for Buffer<T, LENGTH> {
    fn from(buf: [T; LENGTH]) -> Self {
        Buffer { buf }
    }
}
// save a lot of boilerplate
fn main() {
    let buf = Buffer::from([0, 1, 2, 3]);
    dbg!(&buf);
}
```
