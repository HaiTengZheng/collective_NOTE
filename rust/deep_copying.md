# copies of data structures
- shallow   copying a pointer or creating a reference (don't exist in Rust)
- deep      copying or cloning all the values within a structure, recusively

# cloning
used to describe the process of creating a new data structure and cloning all 
    the data from the old structure into new one.
## method
- clone()
comes from the `Clone` trait
can be automatically derived using the `#[derive(Clone)]` attribute
## others
- Functions that take immutable references and return a reference or slice are
    unlikely to make copies (e.g., fn func(&self) &self)
- Functions that take a reference (i.e., &) and return an owned object, it may
    be creating a copy (e.g., fn func(&self) String)
- Functions that take a mutable reference (i.e., &mut), it may be modifying data
    in place (e.g., fn func(&mut self))
- Functions that take a owned object and return an owned object of the same type
    are probably making a copy (e.g., fn func(String) String)
- Functions that take a mutable owned object and return an owned object of the
    same type may not be making a copy (e.g., fn func(mut String) String)
