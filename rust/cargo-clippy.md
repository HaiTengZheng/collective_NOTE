# install 
> rustup component add clippy

# config
```toml
# .clippy.toml
# 允许 main 函数有未使用的变量
allow_unused_variables_in_main = true

# 禁用特定 lint
warn_about_specific_lints = ["clippy::unwrap_used"]
```

# clippy
> cargo clippy --bin binary
- --bin
- --lib
- --test

## warning level
```rust
#![deny(clippy::all)] // 启用所有 Clippy 检查，将警告级别提升为错误
#![deny(clippy::pedantic)] // 启用所有 pedantic 检查，将警告级别提升为错误


// 可以在代码中使用属性来禁用某个检查：
#[allow(clippy::unwrap_used)]
fn main() {
    let maybe_number: Option<i32> = Some(42);
    let number = maybe_number.unwrap(); // Clippy 不会报告这里使用了 unwrap
}
```
