A single CPU can only run one process at a time.

The kernel uses the `process scheduler` to determine which process to run at any
given time.

The scheduler controls the order of running based on the scheduling priority
policy assigned to each thread and process. 
The scheduler divided into two gropus:
- non-real-time policies
- real-time policies

The priority of the process using real-time policies is value between 1 (lowest)
and 99 (highest) and is known as a `static policy`.

The priority of the process could increase or decrease during the lifetime of 
the process is known as `dynamic priority`.
