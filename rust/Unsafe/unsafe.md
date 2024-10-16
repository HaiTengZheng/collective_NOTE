# 隐藏使用端 unsafe 代码块
将 unsafe 从函数签名前移动到其内部，这种方法在表面上提供了安全的 API。
```rust
fn get_value(i: *const i32) -> i32 {
    unsafe {
        *i
    }
}

// 参考 String 的 insert 方法
#[cfg(not(no_global_oom_handling))]
#[inline]
#[stable(feature = "rust1", since = "1.0.0")]
pub fn insert(&mut self, idx: usize, ch: char) {
    assert!(self.is_char_boundary(idx));
    let mut bits = [0; 4];
    let bits = ch.encode_utf8(&mut bits).as_bytes();

    // 如此处般
    unsafe {
        self.insert_bytes(idx, bits);
    }
}

#[cfg(not(no_global_oom_handling))]
unsafe fn insert_bytes(&mut self, idx: usize, bytes: &[u8]) {
    let len = self.len();
    let amt = bytes.len();
    self.vec.reserve(amt);

    unsafe {
        ptr::copy(self.vec.as_ptr().add(idx), self.vec.as_mut_ptr().add(idx + amt), len - idx);
        ptr::copy_nonoverlapping(bytes.as_ptr(), self.vec.as_mut_ptr().add(idx), amt);
        self.vec.set_len(len + amt);
    }
}
```
