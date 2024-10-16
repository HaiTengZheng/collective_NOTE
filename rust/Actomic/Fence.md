# Func: `fence`
> std::sync::atomic::fence

## Atomic fence
1. release fence (`Release`)
2. acquire fence (`Acquire`)
3. both (`AcqRel` or `SeqCst`)

The `SeqCst fence` additionally also takes part in the sequentially consistent
total order. 

An atomic fence allows you to separate the memory ordering from the atomic 
operation.(Using a separate fence can result in an extra processor instruction,
which can be slightly **less efficient**)

A **release-store** can be split into a release fence followed by a (relaxed) 
store.
```rust
a.store(1, Release);
// equal to
fence(Release);
a.store(1, Relaxed);
```

An **acquire-store** can be split into a (relaxed) load followed by an acquire
fence.
```rust
a.load(Acquire);
// equal to 
a.load(Relaxed);
fence(Acquire);
```

A single fence can be used for multiple variables at once.(fence is not tied to 
any single atomic variables)

```rust
// Thread 1
fence(Release);
a.store(1, Relaxed);
b.store(1, Relaxed);

// happeds-before relationship is created

// Thread 2
a.load(Relaxed);
b.load(Relaxed);
fence(Acquire);
```

## Fence conditional
A fence can happen in between, including control flow.
```rust
let p = PTR.load(Relaxed);

if p.is_null() {
    println!("no data");
} else {
    fence(Acquire);
    println!("data = {}", unsafe { *p });
}
```
This can be beneficial: if the pointer is often expected to be null, to avoid
acquire memory ordering when not necessary.

A sequentially consistent operation cannot be split into a relaxed operation
and a memory fence.
