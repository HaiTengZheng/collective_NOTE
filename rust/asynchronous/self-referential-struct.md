# Self-referential struct
`A self-referential struct` is a struct that takes a reference to self and 
stores it in a filed.

There's no way to take a reference to self in Rust and store that reference in 
self. To do this in safe Rust, you have to cast the reference to a pointer 
(Remember that references are just pointers with a special meaning in the 
programming language.)

```
    *********************
    *       struct      *
    *********************
 +----->a: [char; n]    *
 |  *********************
 +------b: *const char  *
    *********************
```

