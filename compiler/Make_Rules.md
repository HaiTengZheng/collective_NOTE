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

## implicit rules
> either pattern rules or suffix rules found in the rules databases
    bouilt-in to make

## static pattern rules
> like regular pattern rules expect the apply only to a specific list of target
    files
