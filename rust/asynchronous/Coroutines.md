# Stackless coroutines
A stackless coroutine is a way of representing a task that can be interrupted and
resumed. (pause and resume the task)
In its simplest form, a coroutine is just a task that can stop and resume by
yielding control to either its caller, another coroutine, or a scheduler.
> Rust doesn't come with a runtime and only provides the infrastructure you need
to create coroutines that have native support in the language.

# Save state in a data structure
A state machine in its simplest form is a ==data structure== that has a predetermined
set of states it can be in.
- Each state represents a possible pause/resume point.
Advantages: Efficient and Flexible
Disadvantages: no one want to write it by hand

# Generators vs Coroutines
Generators are state machines.
Generators are usually limited to yielding to the calling functions,
Coroutines can yield to another coroutine, a scheduler, or simply the caller.(based on what they yield to)
