# meta programming

# syntatic macros (macros-by-example)
- These macro are represented in the compiler's abstract syntac tree output
  along with other pieces of program code.
## defined by another macro `macro_rules!`
```rust
macro_rules! println {
    ($fmt:expr) => (print!(const!(fmt, "\n")));
    // variable: $fmt
    // expr: expression
    ($fmt:expr, $($arg:tt)*) => (print!(concat!($fmt, "\n"), $($arg)*));
    // `$($arg:tt)*` zero or more arguments, the arguments stored in $arg
    // tt: token tree
}
```

# procedural macros (compile plugins)
- These are much more powerful than syntatic macros, allowing any custom rust
  code to be run along the compilation process.
- more complex to implement and rely on the compiler internals
- a limit form : `macros 1.1`
