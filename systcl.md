# on boot, the kernel loads the tunable setting from the configuration files
- /etc/sysctl.d/
- /run/sysctl.d/
- /usr/lib/sysctl.d/

# sysctl
e.g.,
> echo "net.ipv4.icmp_echo_ignore_all=1" > /etc/sysctl.d/ping.conf
## apply the setting
> sysctl -p /etc/sysctl.d/ping.conf
## list kernel tunables
> sysctl -a
