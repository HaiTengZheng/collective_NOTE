# std::thread
```rust
use std::thread;

fn main() {
    thread::spawn(|| {
        // 对 spawn 的调用会创建线程并立即返回，线程开始并发执行而不会阻塞后面
        // 的指令，子线程是以分离状态创建的
        println!("Thread!");
    });
}
```

## spawn()
返回 JoinHandle 类型的值，这种类型是子线程的句柄，可用于连接线程。

## join()
子线程调用，阻塞当前线程，并在执行 join 调用之后的任何代码行之前等待子线程完成
返回 Result

# 自定义线程
> Builder::new()
