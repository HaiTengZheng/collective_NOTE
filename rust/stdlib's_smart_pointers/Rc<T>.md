# Rc<T>
reference counted
- enable shared ownership of a value, allowing multiple parts of your code to 
  have read-only access to the same data without having to clone it
- not thread-safe
- doesn't support interior mutability out of the box

# use scenarios 
- implementing tree-like data structures
- storing shared configuration data
- sharing large, immutable data structures
