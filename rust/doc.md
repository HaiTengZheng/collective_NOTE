# cargo
> cargo doc
## --no-deps 忽略生产依赖项的文件
> cargo doc --no-deps

# 符号
由 rustdoc 解析
#[doc="your doc comment"] 的语法糖, doc attribute
## 元素级
适用于模块中的元素
- ///
- /* */
## 模块级
出现在根层级的注释
- //!
- /*! */

# markdown
```rust
//! ```
//! let work_a = 4;
//! let work_b = 4;
//! ```

/// ```
/// assert!(1);
/// ```
```

# doc attribute
## 软件包级
- #![doc(html_logo_url="")]
- #![doc(html_root_url="")]
- #![doc(html_playground_url="")]
## 元素级别
- #[doc(hidden)]
- #[doc(include)]

 
