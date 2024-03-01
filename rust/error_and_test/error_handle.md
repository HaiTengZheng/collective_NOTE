# error
- 可恢复错误：可以被捕捉的且能够合理解决的问题
- 不可恢复错误：会导致程序崩溃的错误

# Option<T>
用于处理有值与无值的情况
```rust
pub enum Option<T> {
    None,
    Some(T),
}

let warpped_i32 = Some(2);
let empty: Option<i32> = None;
let empty_turbofish = None::<i32>;
```
## 检查变体
- 模式匹配
- if let
```rust
let value = match map.get("one") {
    Some(val) => val + 1,
    None => 0
}
```
## unwrap()
## ?
? is shorthand for "return early with an error result" if the result is not OK
## map()
```rust
fn process(food: Option<Food>) -> Option<Cooked> {
    food.map(|f| Peeled(f))
        .map(|Peeled(f)| Chopped(f))
        .map(|Chopped(f)| Cooked(f))
}
```
## and_then()
```rust
fn cookable_v2(food: Food) -> Option<Food> {
    have_ingredients(food).and_then(have_recipe)
}
```
********************************************************************************
# Result<T, E>
用于处理可恢复错误的情况
```rust
enum Result<T> {
    Ok(T),
    Err(E),
}
// 该类型自动被 Rust 引入
// e.g. T : std::fs::File 
//      E : std::op::Error
let _my_result: Result<_, ()> = Ok(64);
//or 
let _my_result = OK::<_, ()>(64);
let _my_error = Err::<(), f32>(34.5);
let _other_err: Result<bool, String> = Err("Wait, what ?".to_string());
// 别名隐藏
// Result<File>
type Result<T> = Result<T, std::io::Error>;
```
## unwarp() 方法
Ok -> 返回 Ok 中的值
Err -> 自动做 Panic 处理并输出默认的错误消息
## expect() 方法
panic on an unexpected result,
the expect() takes a message as an argument explaining why the program panicked,
it is s safer alternative to unwrap()
具备 unwarp 的功能，允许自定义错误信息，同时显示源文件发生异常时的确切代码行号，
这样更易于追踪导致程序错误的原因
## as_ref()
将 Result<T, E> 转化为 Result<&T, &E>
## as_mut()
将 Result<T, E> 转化为 Result<&mut T, &mut E>
## unwarp_or_else() 方法
Err -> 执行一个闭包
## 传播错误
当函数中包含可能会失败的操作时，除了在这个函数中处理错误外，还可以把处理错误的
    选择权交给该函数的调用者，因为调用者可能拥有更多的信息或逻辑来决定应该如何
    处理错误。
## ?
`?` 操作符可以用于返回值类型为 Result 的函数中，它被定义为与 match 模式匹配有着
    完全相同的工作方式。
Ok -> 返回 Ok 中的值并继续执行下面的代码
Err -> Err 中的值作为整个函数的返回值传给调用者
`?` 与 match 的不同：`？` 使用的错误值会被传递给 from 函数，它定义于标准库中的
    From trait，用于将错误从一种类型转换到另一种类型。因此，`？` 收到的错误类型
    会被转换为当前函数要返回的错误类型
可用链式方法简化代码
```rust
File::open("hello.txt")?.read_to_string(&mut s)?;
```

# Panic
用于处理不可恢复错误的情况
`panic` means to raise an error and abort the program.
```rust
panic!(); // force a panic
compile_error!(); // induce a compile-time error
```
## backtrace
是执行到目前位置为止所有被调用函数的类表，其中有自己编写的函数，也有 Rust 核心
    代码和标准库代码中的函数。
## panic::cat_unwind 函数
捕获 Panic，以便程序可以继续执行而不被终止。应该避免滥用 catch_unwind 作为处理
    错误的惯用方法，因为可能导致内存不安全。

# Abort
用于处理会发生灾难性后果的情况
```toml
[profile.release]
panic = "abort"
```

# 组合器
## map
允许将表示成功的值 T 转换为另一个值 U
```rust
pub fn map<U, F>(self, f: F) -> Option<U>
where F: FnOnce(T) -> U {
    match self {
        Some(x) => Some(f(x)),
        None => None,
    }
}

pub fn map<U, F>(self, f: F) -> Option<U>
where F: FnOnce<T> -> U {
    match self {
        Ok(t) -> Ok(f(t)),
        Err(e) -> Err(e),
    }
}
```
## method
- map_err
- and_then
- unwrap_or
- unwrap_or_else
- as_ref
- as_mut
- or/or_else

## Option 和 Result 类型之间的转换
- ok_or     将 Option 值转化为 Result 值，同时将错误值作为第二个参数进行接受
- ok_or_else    更优，会接受闭包来进行惰性求值
- ok        将 Result 转化为调用 self 的 Option，并且会丢弃 Err 值
