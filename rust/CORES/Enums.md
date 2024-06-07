# Enums
Define a set of related values that a variable can take.

## Data enumeration (enum with data)
```rust
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}
```
