# HashMap<K, V>
存储了 K 类型到 V 类型值之间的映射关系
- 将数据存储在堆上

```rust
use std::collections::HashMap;

let mut scores = HashMap::new()
// .new() 创建一个空
scores.insert(String::from("Blue"), 10);
// .insert() 插入键值对

let teams = vec![String::from("Bule"), String::from("Yellow")];
let initial_scors = vec![10, 50];
let scores: HashMap<_, _> = teams.iter().zip(initial_scors.iter()).collect();
// 通过 .collect() 创建
// HashMap<_, _> 指明数据结构，_ 占位，Rust 能根据动态数组自动推出类型

let score_1 = scores.get(&team_name);
// .get() 返回一个 Option<&V>

scores.entry(String::from("Yellow)).or_insert(50);
// .entry 检测键是否存在一个值，不存在则使用 .or_insert() 插入一个值
```
