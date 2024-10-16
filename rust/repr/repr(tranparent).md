# repr(transparent)
`#[repr(transparent)]` can only be used on a struct or single-variant enum that has a single non-zero-sized field (there may be additional zero-sized fields). The effect is that the layout and ABI of the whole struct/enum is guaranteed to be the same as that one field.
