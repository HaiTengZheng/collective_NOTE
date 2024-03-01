# OODA loop (observe-orient-decide-act)
it offers a structured way to test a hypothesis based on observed data and act
upon it -- that is, a way to get actionable insights from signals.

# observability
assessing the internal state of a system (such as Linux) by measuring external 
information, usually with goal of acting on upon it.

# signal types
different ways to represent and emit information about the state of a system,
either via symbolic means (payload is text, such as the case with logs) or
numerical values (as with metrics) or combinations thereof.

# source
generates signals, potentially of different types

# destination
exposes a user interface (GUI, TUI or CLI) a frontend

# telemetry
the process of extracting signals from sources and transporting (or routing,
shipping) the signals to destinations, often employing agents that collect
and/or preprocesses signals (for example, filter or downsample)
