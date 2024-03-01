# chsh
> change your login shell

## 修改默认的 shell
e.g.
> chsh -s /usr/bin/fish

# find current shell
## in bash
> echo $0 
> ps -p $$
## fish
> ps -p $fish_pid
## both
> echo $SHELL

# list available shells
> cat /etc/shells
> chsh -l

