# LXC
> sudo dnf install lxc
> sudo apt install lxc

# check config
> lxc-checkconfig

# default configuration
> /etc/lxc/default.conf
Container-specific overrides can be configured in an individual container's 
configuration file:
> /var/lib/lxc/{container-name}/config

# bridge
Provide related tools to establish a bridge network
> sudo dnf install bridge-utils
> sudo apt install bridge-utils
file contain the bridge settings:
> /etc/default/lxc-net
```
# edit the `/etc/lxc/default.conf`
lxc.network.type = veth
lxc.network.link = lxcbr0
lxc.network.flags = up
lxc.network.hwaddr = 00:18:5e:xx:xx:xx
# run `sudo systemctl restart lxc-net`
# or `sudo service lxc-net restart`
```
