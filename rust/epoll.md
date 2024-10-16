# epoll
- as long as there is data in the buffer
```rust
pub const EPOLL_CTL_ADD: i32 = 1;
// EPOLLIN represents a bitflag indicating we're insterested in read operations on the file handle
pub const EPOLLIN: i32 = 0x1; 
// EPOLLET represents a bitflag indicating we're insterested in getting events notified with 
// epoll set to an edge-triggered mode
pub const EPOLLET: i32 = 1 << 31;

#[link(name = "C")]
extern "C" {
    pub fn epoll_create(size: i32) -> i32;
    pub fn close(fd: i32) -> i32;
    pub fn epoll_ctl(epfd: i32, op: i32, fd: i32, event: *mut Event) -> i32;
    pub fn epoll_wait(epfd: i32, events: *mut Event, maxevents: i32, timeout: i32) -> i32;
}

#[derive(Debug)]
// #[repr(C)] do what C does
// #[repr(packed)] force Rust to strip any padding, and only align the type to a byte
#[repr(C, packed)]
// A struct used to communicte to the `epoll_ctl` and `epoll_wait`
pub struct Event {
    pub(crate) events: u32, // bitmask
    // Token to identify event
    pub(crate) epoll_data: usize,
}

impl Event {
    pub fn token(&self) -> usize {
        self.epoll_data
    }
}
```

# notify modes 
- Level-triggered (default)
- Edge-triggered
