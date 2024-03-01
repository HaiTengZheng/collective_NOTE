```rust
struct Dog<Breed> {
    name:   String,
    breed:  PhatomData<Breed>
}

let my_poodle: Dog<Poodle> = Dog {
    name: "Jeffrey".into(),
    breed: PhatomData,
}
// Markers let you perform compiler-time optimization or specialization on types
```
