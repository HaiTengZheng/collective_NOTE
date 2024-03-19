# functional design patterns
- Pure functions
- Immutability
- Functional composition
- Higher-order functions (HoF: a function that accepts a function as a parameter)
- Functors (the inverse of functions)
  (A functor defines data, accepts a function, and returns the result of the transformation)
- Monads
```rust
// For our purpose, monads are simply a trait with two methods
trait Monad<A> {
    fn return_(t: A) -> Self;
    //:: A -> Monad<A>

    fn bind<MB, B>(m: Self, f: Fn(A) -> MB) -> MB
    where
        MB: Monad<B>;
    //:: Monad<A> -> (A -> Monad<B>) -> Monad<B>
}
// The first method is the constructor.
// The second method lets you bind an operation to crate another monad.
```
- Function currying (A technique, Rust functions are not curried by default)
  (The difference between curried functions and non-curried functions are that
   curried functions send in parameters one by one, whereas non-curried functions
   send in parameters all at once)
```rust
fn not_curried(p1: u32, p2: u32) -> u32 {
    p1 + p2
}

fn curried(p1: u32) -> Box<Fn(u32) -> u32> {
    Box::new(move |p2: u32| {
        p1 + p2
    })
}

fn main() {
    not_curried(1, 2);
    curried(1)(2);
}
// Curried functions can be used as a function factory. The first few arguments
// configure how the final function should behave. The result is a pattern that
// allows shorthand configuration of complex operators.
```
- Lazy evaluation (It is a pattern)
  (The difference between a normal expression and a lazy expression is that a
   lazy expression will not be evaluated until accessed)
```rust
let y = || { println!("side effect"); 1 + 2}
// For lazy expressions, side effects happen at time of resolution instead of at
// initalization.
// Lazy lists: (0..)
```
- Memoization (a memoized function only computes unique result once)
```rust
#[macro_use] extern crate cached;
#[macro_use] extern crate lazy_static;

cached! {
    FIB;
    fn fib(n: u64) -> u64 = {
        if n == 0 || n == 1 { return n }
        fib(n - 1) + fib(n - 2)
    }
}
```
