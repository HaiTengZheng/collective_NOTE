# lazy_static!
```toml
lazy_static = "1.0"
```
The `lazy_static!` macro helps with this by extending Rust's normal `static`
functionality, which normally requires your objects to be constructable at 
compile-time, with the ability to create lazy objects that are initialized 
during runtime

`lazy_static` 的第三方软件包实现:
- 用于初始化任何能够从程序中的任何位置全局访问的动态类型
- 声明的元素需要实现 `Sync` 特性(意味着如果某个静态值可变，那么必须使用诸如 Mutex
    或 `RwLock` 这样的多线程类型，而不是 `RefCell`)
```rust
use std::sync::Mutex;

lazy_static! {
    static ref ITEMS: Mutex<Vec<u64>> = {
        let mut v = vec![];
        v.push(9);
        v.push(2);
        Mutex::new(v)
    }
}
