# positional parameters
- `$1`
- `$2`
etc

# special parameters
- `$*` and `$@`     (the value of all the positional parameters)
不加引号时 $* 与 $@ 相同。加上引号，则 "$*" 将所有的参数视为单个字符串，
    "$@" 将所有的参数视为不同的独立字符串
- `$#`  (the number of positional parameters)
- `$0`  (contains the path to the currently running script or to
         to tell the shll ifself no script is being executed)
- `$$`  (contains the process identification number (PID) of the current
         process)    
- `$?`  (set to the exit code of the last-executed command)         
- `$_`  (set to the last argument to that command)
- `$!`  (contains the PID of the last command executed in the background)
- `$-`  (set to the option flags currently in effect)
