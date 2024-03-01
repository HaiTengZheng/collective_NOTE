# config file (priority decrement)
1. ANSIBLE_CONFIG
2. ./ansible.cfg
3. ~/.ansible.cfg
4. /etc/ansible/ansible.cfg     (default file, no effective settings)

# important
- for ansible security, a configuration file is never loaded from a
  world-writable directory.


# inventory
files or directories that exist on the sanem system that runs `ansible` and
`ansible-playbook`
> /etc/ansible/hosts
- the location of the inventory can be defined at runtime with the 
  `--inventory-file (-i)` argument or by defining the path in an Ansible 
  `config` file
- can be static or dynamic, or even a combination of both, and Ansible is not
  limited to a single inventory
## static inventories
- a static inventory will consist of a single file in `ini` format, other 
  formats like `YAML` are supported



# library
> /usr/share/ansible

# sudo_user
设置默认执行命令的用户
> sudo_user = root

# forks
设置默认情况下 Ansible 最多能有多少个进程同时工作
default:
> forks = 5 

# remote_port
指定连接被管节点的管理端口, 默认 22
> remote_port = 22

# host_key_checking
设置是否检查 SSH 主机的密匙
> host_key_checking = false

# timeout
设置 SSH 连接的超时间隔, 单位秒
> timeout = 60

# log_path
默认不记录日志
> log_path = /var/log/ansible.log

