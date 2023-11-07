# man pages
> man 5 sshd_config

# config file location
> /etc/ssh/

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# openssh

## secrete key
### version 1
- RSA   (ssh_host_key, ssh_host_key.pub)
### version 2
- RSA   (ssh_host_rsa_key, ssh_host_rsa_key.pub)
- DSA   (ssh_host_dsa_key, ssh_host_dsa_key.pub)

## create version 2 key
> ssh-keygen

## start sshd
> chkconfig ssh on

instantly start
> service sshd start

## transfer
> scp
> sftp

for better
> rsync

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# ed25519
> ssh-keygen -t ed25519

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# ssh-copy-id 
用来实现快速证书的生成及公匙下发
e.g.
> ssh-copy-id -i .ssh/id_ras.pub root@192.168.1.11
