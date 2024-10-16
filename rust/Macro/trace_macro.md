# trace_macros!
It takes a Boolean and globally turns macro tracing on or off

```rust
#![feature(trace_macros, log_syntax)]

trace_macros!(true);

macro_rules! meep {
    () => ();
    ($block:block) => (
        log_syntax!("Inside 2nd branch, block is" $block);
        ($block)
        log_syntax!("Leaving 2nd branch!");
    );
}
```

# log_syntax!
It allows you to log at compile time.
```rust
//! main.rs
#![feature(trace_macros)]
#![feature(log_syntax)]
use crate::greeting::base_greeting_fn;

#[macro_use]
mod greeting;

fn main() {
    trace_macros!(true);
    let _greet = greeting!("Sam", "Heya");
//    println!("{}", greet);
    let _greet_with_default = greeting!("Sam");
//    println!("{}", greet_with_default);
    let _greet_with_default_test = greeting!(test "Sam");
    trace_macros!(false);
}
```
```rust
//! greeting.rs
pub fn base_greeting_fn(name: &str, greeting: &str) -> String {
    format!("{}, {}!", name, greeting)
}

macro_rules! greeting {
    ($name:literal) => {
        base_greeting_fn($name, "Hello")
    };
    ($name:literal, $greeting:literal) => {
        base_greeting_fn($name, $greeting)
    };
    (test $name:literal) => {{
        log_syntax!("The name passed to test is ", $name);
        println!("Returning default greeting");
        base_greeting_fn($name, "Hello");
    }}
}
```
