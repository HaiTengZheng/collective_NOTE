# Box<T>
a smart pointer that allocates menmeory on the heap and allows on the heap and 
allows you to move ownership of a value from the stack to the heap

# use scenarios
```rust
// store large data structure
let data = Box::new([0; 1024]);

// transfer ownership of a value between different parts of your code

// making enum representations more uniform
enum Sizes {
    L,
    XL(Box<[0; 1024>),
    XXL(Box<[0; 1024 * 1024]>),
}

// creating recursive data structures (linked list and trees)

```
