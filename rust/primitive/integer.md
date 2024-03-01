# integer types
- i8, i16, i32, i64, i124
- u8, u16, u32, u64, u124
- isize, usize

# other
- Rust 要求数组索引是 usize，用于表示数组或向量大小或某些数据结构中元素数量的值
  通常也是 usize
- Rust 在调用类型本身的方法之前必须确切地知道一个值属于哪种整形
```rust
(-4).abs() // error
(-4_i32).abs() // true
i32::abs(-4) // true
```

# checked operations
prefix: checked_
- checked_add()
- checked_div()
Return an Option, Some(v) if the mathematically correct result can be 
represented as a value of that type, None if it cannot.

# wrapping operations
prefix: warpping_
- warpping_mul
- warpping_shl
Return the value equivalent to the mathematically correct result modulo the
range of the value

# satutating operations
prefix: satutating_
- satutating_add
- satutating_sub
Return the represented value that is closest to the mathematically correct 
result

# overflowing operations
prefix: overflowing_
- overflowing_sub
- overflowing_add
Return a tuple (result, overflowed), where result is what the wrapping version
of the function would return, and overflowed is a bool indicating whether an 
overflow occured


