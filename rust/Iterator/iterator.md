# iterator
lazy
```rust
// >> std::iter::Iterator   trait
let v = vec![1, 2];
let v_iter = v.iter();
assert_eq!(v.next(), Some(&1));
assert_eq!(v.next(), Some(&2));
assert_eq!(v.next(), None);

// `&` the basic array type does not implement the Iterator trait
// but a reference to the array is a slice, and slice implement the 
// `IntoIterator` trait
for elm in &arr {
    println!("{}", elm);
}
```
- .iter()       For an iterator of references
- .iter_mut()   For an iterator of mutable references
- .into_iter()  For an iterator of values (not references)

A `for` loop is an iterator of values,
`for item in iterator` = `for item in iterator.into_iter()`

# .map()
let you do something to every item

# .for_each()
the method lets you do something with every item without creating a new iterator
- `.iter_mut` plus `.for_each` is basically a `for` loop

# .next()
return a `Option`

## Iterator trait
> std::iter::Iterator

```rust
pub trait Iterator {
    type Item;

    fn next(&mut self) -> Option<Self::Item>;
    \\ ...
}
```
iterator are stateful

# methods
- iter()        iterator
- rev()         resverse the iterator
- next()        next element
- get()         (used to get a number that is not close to the end or
                 to the beginning of the slice)
```rust
// 100% sure that the index is always inside the slice
// the `get_unchecked()` will always return something or segfault, so 
// no need to check
// >> slice::get_unchecked
let x = &[1, 2, 4];

unsafe {
    assert_eq!(x.get_unchecked(1), &2);
}

```
- skip()
- take()
- collect()
- skip_while()
- take_while()
- enumerate()
- filter_map()
- step_by()
