# useradd
add user
## /etc/login.defs
control the behavior of the shadow-utils component
```
CREATE_HOME yes
UMASK 077
HOME_MODE 0700
/* in readhat... */
/* as in debian, create with useradd */
```
## useradd on Debian/Ubuntu
> sudo useradd -m -d /home/frank -s /bin/bash frank
- -m creates the home diretory
- -d specifies the home diretory
- -s specifies the frank's default shell

# addusr on Debian/Ubuntu
the extra ability: automatically encrypt a user's home diretory as you crate 
    the account
> the `ecrypts-utils` package
e.g.
> sudo adduser --envrypt-home ex_username
> ecryptfs-unwrap-passphrse
## /etc/adduser.conf


# the `pwquality` module
PAM (Pluggable Authentication Module)
## /etc/pam.d/system-auth
