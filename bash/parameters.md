# positional parameters
- `$1`
- `$2`
etc

# special parameters
- `$*` and `$@`     (the value of all the positional parameters)
- `$#`  (the number of positional parameters)
- `$0`  (contains the path to the currently running script or to
         to tell the shll ifself no script is being executed)
- `$$`  (contains the process identification number (PID) of the current
         process)    
- `$?`  (set to the exit code of the last-executed command)         
- `$_`  (set to the last argument to that command)
- `$!`  (contains the PID of the last command executed in the background)
- `$-`  (set to the option flags currently in effect)
