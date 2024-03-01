# pattern mathcing
a runtime future that enables a variety of nice code flow patterns.
- it enables clean functional programming patterns

# match
a basic pattern starts with `match` keyword

# guard
allow your to match conditionally
- all match cases within the same match {} block should apply to the same type

# ?
handle `Result<T, E>` or `Option<T>`
- For Result<T, E>, the error types of all the functions using the ? must 
  either match the parent function, or provide an implementation of the `From`
  trait so they can be converted to the target error type
## Result<T, E>
ok() method to map to Option<T>,
err() to map to Option<E>
map_err() to map an error to a different type
## Option<T>
ok_or() to map an Option<T> to Result<T, E>
