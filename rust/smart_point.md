# smart pointer
> are data structures that act like a pointer but also have 
    additional metadata and capabilities. 

## the difference between `reference` and `smart pointer`
> references only borrow data, in many cases, smart pointers own the
    data they point to

# Box<T> 
> allocating values on the heap
- a known size
- implements the `Deref` and `Drop`

# Rc<T>
>  a reference counting type that enables multiple ownership

# Ref<T> and RefMut<T>
> accessed through RefCell<T>, a type that enforces the borrowing rules 
    at runtime instead of compile time

# interior mutability pattern
> where an immutable type exposes an API for mutating an interior value

# trait
- Deref
- Drop
## Deref
> allows an instance of the smart pointer struct to behave like a reference so 
    you can write your code to work with either references or smart pointers

- Implementing the Deref trait allows you to customize the behavior of 
    the dereference operator *. By implementing Deref in such a way that a 
    smart pointer can be treated like a regular reference, you can write code 
    that operates on references and use that code with smart pointers too.

## Drop
> allows you to customize the code that’s run when an instance of the smart 
    pointer goes out of scope
