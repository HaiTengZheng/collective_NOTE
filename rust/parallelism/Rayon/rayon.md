# Parallelizing iterators
## ParallelIterator trait
```rust
// par_iter
// par_iter can do everything that a normal iterator does, but in parallel
words.par_iter().for_each(|val| println!("{}", val);
// replace .iter() with .par_iter()
// for moving iterators, use .into_par_iter() instead of .into_iter()
```

