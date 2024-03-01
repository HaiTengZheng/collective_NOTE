```rust
// String + &str
let hello = "hello ".to_string(); // String
let world = "world"; // &str
let hello_world = hello + world;

// clone
let hello_world = hello.clone() + world;

// get modified in place
let mut hello = "hello ".to_string();
let world = "world";
let hello_world = hello.push_str(world);

// format! macro can concatenate any data types that implement the `Display`
// trait
let num = format!("num: {}", 42);

// Default::default()

```
