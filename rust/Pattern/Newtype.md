# The Newtype Pattern
> Rust-specific pattern
It is an extension of `tuple structs` that uses Rust's type system to provide
additional type information or handling of data.

# Advantages
The Newtype pattern solves two classes of problems
1. prevent unit conversions
2. bypass the orphan rule

# Limitations
Every operation that involves the Newtype needs to forward to the inner type.

# Code
```rust
#[derive(Debug)]
struct BitCount(u32);

#[derive(Debug)]
struct ByteCount(u32);

impl BitCount {
    fn to_bytes(&self) -> ByteCount {
        ByteCount(self.0 / 8)
    }
}

impl ByteCount {
    fn to_bits(&self) -> BitCount {
        BitCount(self.0 * 8)
    }
}

fn main() {
    let bits = BitCount(8);
    let bytes = ByteCount(12);

    dbg!(&bits);
    dbg!(&bytes);
    dbg!(bits.to_bytes());
    dbg!(bytes.to_bits());
    dbg!(bits.to_bytes().to_bits());
    dbg!(bytes.to_bits().to_bytes());
}
```
