# tuple
A tuple is a fixed-length sequence of values, and the values can each have
    different types. (essentially a form of syntax suger in Rust)
- tuple in Rust are not reflective: unlike arrays, you can't iterate over a
    tuple, take a slice of a tuple, or determine the type of its components at
    runtime.

e.g.
```rust
let tup1: (i8, f32, bool) = (-10, 7.7, false);
// 元组中的每个元素都有各自的类型。
// 元组的长度固定，一旦定义就不能在增长或缩短。
// "元组名.索引" 的方式访问元组中相应索引位置的元素，索引从 0 开始。
```

# destructuring
```rust
let tup = (2, 3, 4);
let (x, y, z) = tup;
```

# 访问元组中的值
`.` use dot
```rust
tup.1
```
