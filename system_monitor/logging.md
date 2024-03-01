# signal tyeps
signal are how we communicate the state of a system for further processing or
    interpretation

# logs
logs are a fundamental signal types that every system, to some extent, 
    generates.
logs are discrete events with a textual payload, meant for human consumption,
    typically, these events are timestamped.

# metrics
metrics are (usually regularly) sampled numerical data points,, forming a time
    series
## counter
the value of a counter can only ever go up (besides resetting a counter to zero)
## gauges
a gauge value can go up or down
## histograms
a sophisticated way to build a distribution of values. using buckets, histograms
    allow you to access how the data overall is structed. they also enable you
    to make flexible statements (such as 50% or 90% of the values fall into a 
    certain range)

# traces
traces are a dynamic collection of runtime information (for example, 
    information about what syscalls a process uses, or the sequence of events
    in the kernel, for a given cause).
traces are ofthen used not only for debugging but also for performance 
    assessments

# commands
> ls -al /var/log
