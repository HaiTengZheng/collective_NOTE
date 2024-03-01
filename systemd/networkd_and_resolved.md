# systemd
- systemd-networkd
- systemd-resolved

# .network
> /etc/systemd/network/
RHEL distros don't use networkd by default

# systemd-networkd
> sudo dnf install epel-release
> sudo dnf install systemd-networkd
> sudo systemctl disable NetworkManager
> sudo systemctl enable systemd-networkd systemd-resolved
> /etc/resolv.conf

# Netplan on Ubuntu
.yaml
> /etc/netplan
> /run/systemd/network/
e.g., 01-network-manager-all.yaml
```yaml
# a new node
network:
  # unclear
  version: 2
  # use NetworkManager, and all the other configuration is done with the normal
  # NetworkManager files
  # no renderer, use `networkd`
  renderer: NetworkManager
  # defines the network interface
  ethernets:
    enp0s3:
      dncp4: true
```
## command
> netplan try
> netplan apply
