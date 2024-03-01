# crate
Rust 的基本编译单元，分为
- bin   (至少一个)
- lib   (至多一个)
## bin
> cargo new project_name --bin
(--bin is optional)
> src/main.rs
## lib
> cargo new project_name --lib
> src/lib.rs


# Rust 模块文件系统规则
1. 如果 foo 模块没有子模块，将 foo 模块的代码放在 foo.rs 文件中
2. 如果 foo 模块有子模块：
- 将 foo 模块的代码放在 foo.rs 文件中，并将其子模块存放在 foo/ 文件夹 (推荐)
- 将 foo 模块的代码放在 foo/mod.rs 文件，并将其子模块所在文件存放在 foo/ 文件夹


# mod
Rust 通过在 mod 关键字后跟模块名来定义模块，或者引用另一个文件中的模块
```rust
mod chinese {
    mod greetings {}
    mod farewalls {}
}
// lib.rs
// |- chinese
//    |- greetings
//    |- farewalls
//
// 字模块位于父模块的命名空间，可以使用 `::` 来访问字模块
// e.g. chinese::greetings
```
- "mod xxx;" 无法引用多层结构下的模块
> Rust 默认所有的模块及模块中的函数和类型都是私有的，也就是只能在模块的内部使用。
    如果一个模块或者模块中的函数和类型需要为外部使用，必须添加 pub 关键字
## 在文件系统中寻找多层模块的规则
1. main.rs, lib.rs, mod.rs 文件中出现 "mod xxx;", 默认优先寻找同级文件夹下的
    xxx.rs
2. 如果同级文件下的 xxx.rs 文件不存在，则寻找 xxx/mod.rs 文件，即与 xxx.rs 文件
    所在同级文件夹的 xxx 文件夹下的 mod.rs
3. 如果其他文件如 yyy.rs 文件中出现 "mod xxx"，则寻找 yyy/xxx.rs 文件，即与
    yyy.rs 文件所在同级文件夹的 yyy 文件夹下的 xxx.rs 文件
## use
use 可以将指定的模块或函数引入本地作用域，但不会将其子模块也引入。
使用 as 可以对模块或者函数进行重命名

# 模块的路径
- crate     根路径
- self      当前模块
- super     当前模块的父模块
可以使用 `*` 通配符

# pub use
将深层的模块、函数和类型定义导出到上层路径，这在接口设计中会经常用到，可以让外
    部调用更加方便。

# 加载外部 crate
```toml
[dependencies]
phrases_lib { path = "../phrases_lib" }
```
