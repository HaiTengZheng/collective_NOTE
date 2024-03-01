# trait
一个元素，定义了一组类型可以选择性实现的 “契约” 或共享行为
- Rust 中的特征以多种形式存在
- 能在不同类型之间建立关联

## key: trait  
```rust
struct Audio(String);
struct Video(String);

pub trait Playable {// trait 默认私有，使用 use 导入需要调用特征的模块的作用域中
    // 任何可实现的
    fn play(&self);
    // self 只是 Self 的类型别名，它指的是实现特征的类型 
    fn pause() {
        println!("Paused");
    }
}

impl Playable for Audio {
    fn play(&self) {
        println!("Now playing: {}", self.0);
    }
}

impl Playable for Video {
    fn play(&self) {
        println!("Now playing: {}", self.0);
    }
}
```
## 方法
- 关联方法      这些方法可以直接在实现特征的类型上使用，并不需要类型特征的实例来
                调用，也称方法。
- 实例方法      需要将 self 作为其第一个参数，这仅使用于实现特征的类型实例，self
                将指向实现特征的类型特征。三种：self, &self, &mut self

## 
```rust
trait Vehicle {
    fn get_price(&self) -> u64;
}

trait Car: Vehicle { // 特征继承
    fn model(&self) -> String;
}
// 任何实现 Car 的类型必须实现 Vehicle
```
