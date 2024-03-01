# turbofish
a symbol like "::<>"
e.g.,
```rust
use std::str;
// std::str 模块的泛型解析函数 parse 需要使用该符号
let num_from_str = str::parse::<u8>("34").unwrap();
// 只有实现了 FromStr 接口或特征的类型才能传递给 parse 函数
```
