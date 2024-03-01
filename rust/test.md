# 属性
指元素的注释
- #[<name>]     适用于每个元素
- #![<name>]    适用于每个软件包

# 断言宏
## assert!
```rust
assert!(true);
assert!(a == b, "{} was not equal to {}", a, b);
// 可以额外添加格式化字符串，后跟相应数量的变量，用于自定义异常消息
```
## assert_eq!
也可以自定义格式化字符串
## assert_nq!
## debug_assert!
仅在调试版本中有效
## debug_assert_eq!
## debug_assert_nq!

# cargo test
> cargo test --help
> cargo test -- --help
## --nocapture 禁止输出截获功能
> cargo test -- --nocapture
## --test-threads 控制线程数量
> cargo test -- --test-threads=1
## --ignored 单独运行 #[ignore] 类别
> cargo test -- --ignored

# 单元测试
```rust
#[cfg(test)] // 隔离测试代码, cfg (configuration)
// cfg 通常用于条件编译，但不限于测试代码。它可以为不同体系结构或配置标记引用或
// 排除某些代码。

mod tests {
    // mod 封装，隔离代码
    #[test]
    // test 属性用于标记
    fn basic_test() {
        assert!(true);
    }
}
```
> rustc --test name.rs
> cargo test
默认并行运行，修改环境变量 RUST_TEST_THREADS=1 以单线程运行。
> cargo test -- --test-threads=1
## 故障测试
```rust
#[test]
#[should_panic] // 搭配 #[test] 使用，表示函数应该导致不可恢复的故障 (panic)
fn function_test() {
    assert_eq!(1, 2);
}
```
## 忽略测试
```rust
#[test]
#[ignore] // 在执行 cargo test 时忽略此类测试功能
// cargo test -- --ignored 单独测试
```

# 集成测试
/test 目录中单独编写
```rust
use addr;
```
> cargo test --test integration_test
