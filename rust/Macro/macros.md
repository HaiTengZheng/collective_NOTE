# meta programming

# macro
- declarative(recursive) macros    (default)
- procedural macros     (require a flag to enable)
  需要将 Cargo.toml 文件中的属性设置为 proc-macro = true 来生成独立的软件包

Macros execute at compile time.

Rust 宏不会从执行环境中捕获变量

# syntactic macros (macros-by-example)
- These macro are represented in the compiler's abstract syntactic tree output
  along with other pieces of program code.
## defined by another macro `macro_rules!`
```rust
#![feature(trace_macros)] // for debugging macros

macro_rules! println {
    () => { println!("A macro with no arguments")};
    ($fmt:expr) => (print!(const!(fmt, "\n")));
    // variable: $fmt
    // expr: expression
    ($fmt:expr, $($arg:tt)*) => (print!(concat!($fmt, "\n"), $($arg)*));
    // `$($arg:tt)*` zero or more arguments, the arguments stored in $arg
    // tt: token tree
    ($s:stmt) => {println!("A macro with a statement")}
}

#[macro_use]
mod macros {
    macro_rules! my_macro {
        () => {
            println!("Check out my macro!");
        };
    }
}
// The macro_use attribute has two purposes. 
// First, it can be used to make a module's macro scope not end when the module
// is closed, by applying it to a module:
// 
// Second, it can be used to import macros from another crate, by attaching it 
// to an extern crate declaration appearing in the crate's root module. 
```
# $($var:type) pattern
- `*` means that the repeat needs to happen zero or more times
- `+` means that the repeat needs to happen one or more times
## $($x:expr),*
match sequences such as `1, 2, 3` (comma-separated list of expressions)
It won't match a sequence with a trailing comma such as `1, 2, 3,`
## $($x:expr,)*
cpature the comma inside the repeating match, which allows the preceding form.



# procedural macros (compile plugins)
实现为函数，这些函数将接受宏输入作为标记流类型，并在编译时进行相关转换后，将生成
的代码作为标记流返回
- These are much more powerful than syntactic macros, allowing any custom rust
  code to be run along the compilation process.
- more complex to implement and rely on the compiler internals
- a limit form : `macros 1.1`
## `#[proc_macro]
- #[proc_macro] 类函数过程宏
- #[proc_macro_attribute] 类过程宏
- #[proc_macro_derive] 派生过程宏

