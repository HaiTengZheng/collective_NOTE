# integer
- i8, i16, i32, i64, i124       (i   signed)
- u8, u16, u32, u64, u124       (u   unsigned)
- isize, usize                  (platform dependent sizes, 32 or 64 bits)

`usize` is equivalent to C's `size_t` is provided to permit signed arithmetic
    with sizes.
In the Rust standard library, functions returning or expecting a length
    parameter expect a `usize`.

# float
- f32       单精度浮点数，小数点后至少 6 位有效数字
- f64       双精度浮点数，小数点后至少 15 位有效数字

## prefix
- 0b        binary
- 0o        octal
- 0x        hexadecimal
- b         byte literals
- f         float

## suffix declaration
e.g.
112i32
32.323f32

# some rule
- Rust 允许使用下划线 "_" 作为虚拟分隔符来对数字进行可读性分隔  e.g. 500_000

# arithmetic
In Rust, all arithmetic is checked by default.
## wrapping form
Perfoms modular arithmetic and is compatible with the C equivalent operations.
> overflow on signed integers in C is undefined.
