# float
- f32
- f64

# remark
方法的调用优先级高于前缀运算符，因此在堆负值进行方法调用时，务必正确加上圆括号
> (-1.1_f64).floor()

# f32
three field:
- 符号位
- 指数
- 尾数
> IEEE 754-2019 and 754-2008
```rust
// 分离符号位
let n: f32 = 42.42;
let n_bits: u32 = n.to_bits();
let sign_bit = n_bits >> 31;
// 分离指数
let exponent_ = n_bits >> 23;
let exponent_ = exponent_ & 0xff;
let exponent_ = (exponent_ as i32) - 127;
// 分离尾数
let mut mantissa: f32 = 1.0; // 代表隐藏的第 24 位的权重
for i in 0..23 {
    let mask = 1 << i;
    let one_at_bit_i = n_bits & mask;
    if one_at_bit_i != 0 {
        let i_ = i as f32;
        let weight = 2_f32.powf(i_ - 23.0);
        mantissa += weight;
    }
}
///////////////////////////////////////////////////////////////////////////////
const BIAS: i32 = 127;
const RADIX: f32 = 2.0;

fn main() {
    let n: f32 = 42.42;

    let (sign, exp, frac) = to_parts(n);
    let (sign_, exp_, mant) = decode(sign, exp, frac);
    let n_ = from_parts(sign_, exp_, mant);

    println!("{} -> {}", n, n_);
    println!("field\t | as bits\t\t\t | as real number");
    println!("sign\t | {:01b}\t\t\t\t | {}", sign, sign_);
    println!("exponent | {:08b}\t\t\t | {}", exp, exp_);
    println!("mantissa | {:023b}\t | {}", frac, mant);
}

fn to_parts(n: f32) -> (u32, u32, u32) {
    let bits = n.to_bits();
    
    let sign = (bits >> 31) & 1;
    let exponent = (bits >> 23) & 0xff;
    let fraction = bits & 0x7fffff;

    (sign, exponent, fraction)
}

fn decode(
    sign: u32,
    exponent: u32,
    fraction: u32,
) -> (f32, f32, f32) {
    let signed_1 = (-1.0_f32).powf(sign as f32);

    let exponent = (exponent as i32) - BIAS;
    let exponent = RADIX.powf(exponent as f32);

    let mut mantissa: f32 = 1.0;
    for i in 0..23 {
        let mask = 1 << i;
        let one_at_bit_i = fraction & mask;
        if one_at_bit_i != 0 {
            let i_ = i as f32;
            let weight = 2_f32.powf(i_ - 23.0);
            mantissa += weight;
        }
    }

    (signed_1, exponent, mantissa)
}

fn from_parts(
    sign: f32,
    exponent: f32,
    mantissa: f32,
) -> f32 {
    sign * exponent * mantissa
}
```

# 定点数格式
可以用来表示分数，并且是在没有浮点单元 (FPU) 的 CPU 上进行计算的一种选择。
定点数不会为了适应不同的表示范围而移动小数点的位置。
## Q 格式
一种使用单个字节的定点数格式
## Q7
7 位表示数字，1 位表示符号
```rust
#[derive(Debug,Clone,Copy,PartialEq,Eq)]
pub struct Q7(i8);

impl From<f64> for Q7 {
    fn from(n: f64) -> Self {
        // assert!(n >= -1.0)
        // assert!(n <= 1.0)
        if n >= 1.0 {
            Q7(127)
        } else if n <= -1.0 {
            Q7(-12)
        } else {
            Q7((n * 128.0) as i8)
        }
    }
}

impl From<Q7> for f64 {
    fn from(n: Q7) -> f64 {
        (n.0 as f64) * 2_f64.powf(-7.0)
    }
}

impl From<f32> for Q7 {
    fn from(n: f32) -> Self {
        Q7::from(n as f64)
    }
}
```
