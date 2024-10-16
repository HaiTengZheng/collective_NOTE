# runtime
All runtimes in Rust need to do at least two things:
1. schedule
2. drive objects implementing Rust's `Future` trait to completion.

# divide runtime into two parts
1.  `reactor(driver)` tracks events we're waiting on and makes sure to wait to 
    notification from the OS in an efficient manner.
2.  `executor` schedules tasks and polls them to completion.

## reactor
It is simply something that ==reacts to a whole set of incoming events and dispatch
them one by one to handler==.
- It's an event loop (in our case, it dispatches events to an executor).

## executor
An executor simply decides ==who== gets time on the CPU to progress and ==when== they
get it.
- It's a type of scheduler.
- The executor must also call `Future::poll` and advance the state machines to 
their next state.
