# Module std::cell
Shareable mutable containers.

## In a single-threaded way
- `Cell<T>`
- `RefCell<T>`
- `OnceCell<T>`

Each provides a different way of **providing safe interior mutability**.
Each may be mutated through shared references (i.e. the common `&T` type).

# Mutability
- interior mutability (mutable via `&T`)
- inherited mutability (mutable via `&mut T`)
