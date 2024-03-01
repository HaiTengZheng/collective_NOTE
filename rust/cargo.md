# 版本
> cargo add actix-web@4
```toml
actix-web = "4"
```

# 特性
> -F    (--features)
When adding multiple crates, the features for a specific crate may be 
enabled with package-name/feature-name syntax. This flag may be specified 
multiple times, which enables all specified features.
e.g.
> cargo add tokio@1 -F tokio/macros -F tokio/rt-multi-thread
> cargo add tokio@1 --features macros,rt-multi-thread
```toml
tokio = {version = "1", features = ["macros", "rt-multi-thread"]}
```
- cfg(predicate): instruct the compiler to only compile the thing its attached
  to if the predicate is use
- cfg_attr(predicate, attributed): instructs the compiler to only enable the
  specified attribute if the predicate is true
```rust
#[cfg(feature = "serde")]
use serde::{Deserialize, Serialize};

#[cfg_attr(
    feature = "serde",
    derive(Serialize, Deserialize, Zeroize, Debug, PartialEq)
)]

#[cfg_attr(
    not(feature = "serde"),
    derive(Serialize, Deserialize, Zeroize, Debug, PartialEq)
)]
```

# cargo check
check if code compiles or not


# switch between toolchains
use the `+channel` options
channels:
- stable
- beta
- nightly
> cargo +nightly expand
## override option with rustup
> rustup override set nightly

# cargo new
Applications use src/main.rs as their entrypoint, and libraries use src/lib.rs
as their entrypoint
## --bin
create an executable project
> cargo new --bin hello_world
## --lib
> cargo new --lib
create a new library
## --vcs

# add crates
major.minor.patch
e.g.
> cargo add rand
- ^x.y.z
- ~x.y.z
- *,x.*
- >=x, <x.y, =x.y.z
Cargo uses the semver crate for parsing the versions specified.

# cargo.lock
- For libraries, it's recommended you do not include this file in your version
  control system. When using Git, you can do this by adding Cargo.lock to 
  .gitignore. Leaving out the lock file allows downstrem packages to update
  indirect depencies as needed.
- For applications, it's recommended you always include Cargo.lock alongside 
  Cargo.toml. This helps to ensure consistent behaviour in published release,
  should 3rd party libraries change in the future.

# run
> cargo run
## -p 
specify the package in the workspace you want to run
> cargo run -p


# build
> cargo build
> cargo build --release

# cargo.toml
```toml
[workspace]
members = [ workspace_1, workspace_2 ]

[profile.dev]
opt-level = 0

[profile.release]
opt-level = 3
```
## workspace
workspace 是一组 crate，它们共享着公共构建目录和 Cargo.lock 文件
> cargo build --workspace

# cargo
cargo build -> [profile.dev]
cargo build --release -> [profile.release]
cargo test -> [profile.test]

# package
> cargo package
> cargo package --list
> cargo login
> cargo publish
```toml
# 提供 path 和 version
image = { path = "vendor/image", version = "0.1" }
```
