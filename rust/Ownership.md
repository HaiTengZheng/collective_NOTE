# ownership
## rules
- every value has an owner
- there can only be one owner at a time
- when the owner goes out of scope the value is dropped

-------------------------------------------------------------------------------
# reference


-------------------------------------------------------------------------------
# borrowing
- using the `&` operator
- using the `&mut` operator

## methods
- as_ref()
- as_mut()
`as_ref()` and `as_mut()` are often used by container types to provide access
    to internal data, rather than obtaining a reference to the container itself.

## traits
- AsRef
- AsMut