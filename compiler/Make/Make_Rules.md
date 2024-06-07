# rules
> building and process `dependency graph`
> a rule can have more than one target, if the target are out of date, the same
    set of actions will be performed to update each one
> If either object file is out of date with respect to any of its
    prerequisites, make will update the object file by executing the commands
    associated with the rule
> a rule doesn't have to be defined "all at once"

## explicit rules
> use explicit filenames

## pattern rules
> use whildcards instead of explicit filenames
模式出现在工作目标或必要条件中时，是由 make 进行通配符的扩展，出现在命令时，
是由 subshell 进行扩展的动作。
make 在读取 makefile 的时候立即扩展通配符，但 shell 只会在执行命令的时候扩展通配符。

## implicit rules
> either pattern rules or suffix rules found in the rules databases
    bouilt-in to make

## static pattern rules
> like regular pattern rules expect the apply only to a specific list of target
    files


# wildcard (globbing)
- `*`       all
- `.`       single character
- `[...]`   character class
- `[^...]`  complement
- `~`       home directory
