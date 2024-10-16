# Pinning
It's a part of Rust's standard library and consist of two parts:
1.  the type: `Pin`
2.  the marker-trait: `Unpin`

-   Pinning is only a language construct. It's only a part of the type system
    that prevent us from being able to move a value.
-   `Pin` does not remove the need of `unsafe` - it just gives the user of 
    unsafe a guarantee that the value has a stable location in memory, so long
    as the user that pinned the value uses safe Rust. It makes sure that all
    operations that can lead to problems must use `unsafe`.
-   At a very high level, pinning makes it possible to rely on the data that has a
    stable memory address by disallowing any operation that might move it.

# Pin<T>
```rust
// std::pin
#[repr(transparent)]
pub struct Pin<P> { /* private fields */ }
```
`Pin` wrap types that implement the `Deref` trait, which in practical terms
means that it wraps ==references and smart pointers==.

# Unpin
A marker trait.
```rust
pub auto trait Unpin { }
```
即使类型实现了 Unpin 其依然可以 Pin 然而不会有任何效果，该值一样可以被移动。
`Pin<&mut u8>` is equal to `&mut u8`

If a type implements `Unpin`, pinning will have ==no effect== on that type.

The impressive thing is that almost everything implements `Unpin` by default,
and if you manually want to mark a type as `!Unpin`, you have to add marker
trait called `PantomPinned` to your type. Having a type, `T`, implement `!Unpin`
is the only way for something such as `Pin<&mut T>` to have any effect.


-   Pinning a type that's `!Unpin` will guarantee that the value remains at the 
    same location in memory until it gets dropped, so long as you stay in safe
    Rust.

-   `Pin projections` are helper methods on type that's pinned. They're only
    valid on pinned instances of ==self==, e.g., `foo(self: Pin<&mut self>)`.


-   `Structural pinning` is connected to `pin projections` in the sense that,
    if you have `Pin<&mut T>` where T has one filed, `a`, that can be moved
    freely and one that can't be moved, `b`, you can do the following:
1.  Write a `Pin projection` for a with the `fn a(self: Pin<&mut self>) -> &A`
    signature. In this case, we say that pinning is `not structural`.
2.  Write a projection for b that looks like `fn b(self: Pin<&mut self>) -> Pin<&mut B>`,
    in which case we say that pinning is `structural` for b since it's pinned when
    the struct, T, is pinned.
