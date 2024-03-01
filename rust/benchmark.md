# bench
```rust
#![feature(test)]
extern crate test; // 必须在 test 前使用 extern test 来声明内部软件包测试以及
                   // #![feature(test)] 属性注释


use test::Bencher;

pub fn do_nothing_slowly() {
    print!(".");
    for _ in 1..10_000_000 {};
}

pub fn do_nothing_fast() {
}

#[bench] // 表示是一个基准测试
fn bench_nothing_slowly(b: &mut Bencher) {
    b.iter(|| do_nothing_slowly());
}

#[bench]
fn bench_do_nothing_fast(b: &mut Bencher) {
    b.iter(|| do_nothing_fast());
}

```
- 内部编译器软件包 libtest 包含一个 Bencher 类型，基准函数通过它在多次迭代中运行
  相同的基准代码，此类型是针对编译器内部的，只适用于测试模式
> cargo +nightly bench
or
> rustup update nightly             // install
> rustup override set nightly       // override
> cargo bench

# criterion
稳定版上的 Rust bench
> cargo add --dev criterion 
```toml
// Cargo.toml
[dev-dependencies]
criterion = "0.1"

[[bench]]
name = "fibonacci"
harness = false
```
/benches/fibonacci.rs 文件位置
```rust
#[macro_use] // 意味着要使用来自此软件包的任何宏时，我们需要使用此属性来选择它，
             // 因为默认情况下它们是非公开的。
extern crate criterion;
extern crate criterion_demo;

use criterion_demo::{fast_fibonacci, slow_fibonacci};
use criterion::Criterion;

fn fibonacci_benchmark(c: &mut Criterion) {
    c.bench_function("fibonacci 8", |b| b.iter(|| slow_fibonacci(8)));
}

criterion_group!(fib_bench, fibonacci_benchmark);
criterion_main!(fib_bench);
```
> cargo bench

