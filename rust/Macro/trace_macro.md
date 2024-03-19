# trace_macros!
takes a Boolean and globally turn macro tracing on or off

# log_syntax!

```rust
#![feature(trace_macros, log_syntax)]

trace_macros!(true);

macro_rules! meep {
    () => ();
    ($block:block) => (
        log_syntax!("Inside 2nd branch, block is" $block);
        ($block)
        log_syntax!("Leaving 2nd branch!");
    );
}
```
