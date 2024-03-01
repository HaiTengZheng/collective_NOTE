# ?
is shorthand for "return early with an error result" if the result is not OK

# properties
- Funtions which might fail should return a `Result`
- Funtions which may return no value (i.e., null) should return an `Option`

# expect()
panic on an unexpected result
- it takes a message as an argument explaning why the program pancked
- is a safer alternative to `unwrap()`

