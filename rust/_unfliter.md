# unit type
> like an empty value and is signified with a set of empty parentheses: ()

# Self
`Self` is the type of the `self` value.

# ... syntax
represents an inclusive range
```rust
match c {
    b'a'...b'z' => c - 32,
    _ => c,
}

# import the crate
```rust
extern crate sdl2;
```
# Exception-driven development

# RALL (Resource Acquisition Is Initialization)

# ORM (Object Relational Mapping)

# 字符类型
UTF-8  作为底层编码，每个字符占 4 个字节。

# 范围区间
(1..5)        =>          1, 2, 3, 4
(1..=5)       =>          1, 2, 3, 4, 5
`.rev()` 方法可以将范围内的数字反转
`.sum()` 方法可以对范围内的数字求和

```rust
#![no_std]
// indicates that this program will not link to the standard crate, `std`. 
// Instead it will link to its subset: the `core` crate
#![no_main]
// indicates that this program won't use the standard main interface that most
// Rust programs use. The main reason to go with `no_main` is that using the `main`
// interface in `no_std` requires nightly
```


# the nonfunctional style (called imperative style)
imperative means give order or instructions

# 
- snake_case
- UpperCarmelCase
- SCREAMING_SNAKE_CASE
- ' tick
