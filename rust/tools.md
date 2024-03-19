# docs
## install the docs commponent
> rustup commponent add rust-docs
## open the docs from the standard library
> rustup doc --std
## generate docs from your codebase
> cargo doc --open
--------------------------------------------------------------------------------
# clippy (the rust official linter)
> rustup commponent add clippy
## fail the linker check if clippy emits any warnings
> cargo clippy -- -D warnings
## attribute
- #![allow(clippy::lint_name)]
- #[allow(clippy::lint_name]

# fast linking
> sudo dnf install lld clang
```toml
[target.x86_64-unknown-linux-gnu]
rustflags = ["-C", "linker=clang", "-C", "link-arg=-fuse-ld=lld"]
```
--------------------------------------------------------------------------------
# cargo-watch
monitors your source code to trigger commands every time a file changes
> cargo install cargo-watch
--------------------------------------------------------------------------------
# code coverage
> cargo install cargo-tarpaulin
## Run tests only
> cargo watch -x test
## Run check then tests
> cargo watch -x check -x test
## Run run with arguments
> cargo watch -x 'run -- --some-arg'
## Run an arbitrary command
> cargo watch -- echo Hello world
## Run with features passed to cargo
> cargo watch --features "foo,bar"
--------------------------------------------------------------------------------
# formatting
> rustup commponent install rustfmt
## format whole project
> cargo fmt
## fail then a commit contains unformatted code, printing the difference to the console 
> cargo fmt -- --check
--------------------------------------------------------------------------------
# security vulnerabilities
> cargo install cargo-audit
> cargo audit

