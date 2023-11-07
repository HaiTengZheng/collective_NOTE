# -F    --features
When adding multiple crates, the features for a specific crate may be enabled with package-name/feature-name syntax. This flag may be specified multiple times, which enables all specified features.
e.g.
> cargo add tokio -F tokio/macros -F tokio/rt-multi-thread

# use the nightly toolchain just for this command invocation
e.g.
> cargo +nightly expand
