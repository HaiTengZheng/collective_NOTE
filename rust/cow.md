# Cow
a Clone on Write wrapper around a type which means it will try to borrow a type
for as long as possible and only make an owned clone of the data when absolutely 
necessary, which happens at the first mutation
```rust
use std::borrow::Cow;
struct NameLength<'a> {
    name: Cow<'a, str>,
    length: usize,
}

impl<'a> NameLength<'a> {
    fn new<S>(name: S) -> Self
    where
        S: Into<Cow<'a, str>>, 
    {
        let name =: Cow<'a, str> = name.into();
        NameLength {
            length: name.len(),
            name,
        }
    }
}
```
