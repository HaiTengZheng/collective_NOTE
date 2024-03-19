# Functional Programming (FP)
A broad definition: functional programming emphasizes the use of composable and
maximally reusable functions to define program behavior.
- closures: A closures is an boject that acts as function, impleting 
  `fn`, `Fn`, `FnMut` or `FnOnce` 
```rust
// simple closures can be defined with the built-in closure syntax
(0..100).map(|x| x * x)
// closures can also have complex bodies with statements if the block syntax is 
// used
(0..100).map(|x| {
    fn (y: u32) -> u32 {
        y * y
    }
    let z = f(x + 1) * f(x + 2);
    z * z
})
// It is possible to define funxtions or methods that accept closures as 
// arguments, to use the closure as a callable function, a bound of `Fn`, 
// `FnMut`, or `FnOnce` must be specified
fn f<T>(g: T, x: u32) -> u32
where
    T: Fn(u32) -> u32
{
     g(x + 1) * g(x + 2)
}

fn main() {
    f(|x| { x * x}, 2);
}
```
- iterators

# higher order functions
Functions which take other functions as parameters
- fn
- Fn
- FnMut
- FnOnce
These traits are automatically implemennted if permitted
