# use borrowed types for arguments
1. Alaways prefer using the `borrowed type` over `borrowing the owned type`.
- &str over &String
- &[T] over $Vec<T>
- &T over &Box<T>
