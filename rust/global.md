# const
e.g.,
> const HEADER: &'static [u8; 4] = b"OBJ\0";
常量表示具体值，并且没有与之关联的任何内存位置，无论它们在何处使用都会被内嵌

# static
e.g.,
> static mut BAZ: u32 = 4;
具有固定的内存位置，并且在整个程序中作为单个（唯一）实例存在
- 读取和写入静态值都必须在某个 unsafe 代码块中完成
- 通常与同于原语搭配使用，还用于实现全局锁定，以及与 C 程序库集成

# const fn
- 纯函数，必须可重现(意味着不能将可变参数带入任何类型，也不能包含动态的操作)
- 对编译期执行的操作非常有用
```rust
const fn read_header(a: &[u8]) -> (u8, u8, u8, u8) {
    (a[0], a[1], a[2], a[3])
}
const FILE_HEADER: (u8, u8, u8, u8) = 
    read_header(include_bytes!("./const_fn_file.rs"));
// include_bytes! 接受一个文件作为字节数组，它也会在编译期读取文件
```

