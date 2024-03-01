# Ownership

# Rules
- Each value in Rust has a variable that's called its owner
- There can be only one owner at a time
- When the owner goes out the out of scope, the value will be dropped
## String
this type is allocated on the heap and as such is able to store an amount of
    text that is unknown to us at compile time.


# move
The basic types implement a special marker: `Copy`. `Copy` types are copied
    intead of moved
```rust
#[derive(Clone, Copy)]
/* Copy require Clone.
 * We can't derive Copy for a type containing a value that doesn't implement
 * Copy.
 */
```
