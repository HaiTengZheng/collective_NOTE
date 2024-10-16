# `#[repr(transparent)]`
Documenting the transparent representation.

`1-ZSD`: types that are one-aligned and zero-sized

It can only be used to a `struct` or an `enum` with single variant that has:
1. a single filed with non-zero zero-size
2. any number of fields with size 0 and alignment 1 (e.g., `PhantomData<T>`)


A struct with the representation with a primitive field will have the ABI for 
the primitive field.
