# Mutex<T>
a smart pointer in Rust that provides exclusive, mutable access to data in a
multi-threaded environment
- Mutex is short for mutual exclusion, and is used to protect shared data from
  data races and other concurrency-related issues
- only one thread can access the data at a time, whether it is for reading or 
  writing
