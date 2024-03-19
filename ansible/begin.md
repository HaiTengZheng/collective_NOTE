> sudo dnf install ansible
> mkdir ansible
> cd ansible
> nvim ansible.cfg
```
[defaults]
inventory = inventory
```
> ssh-keygen -t rsa -b 2048
> ssh-copy-id -i id_rsa.pub localhost
> nvim inventory
```
[workstation]
localhost
[workstation:vars]
ansible_ssh_private_key=/home/mustang/ansible/id_rsa
```
> ansible all -m ping
> ansible workstation -a "hostname"
