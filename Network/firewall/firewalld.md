# firewalld D-Bus interface
tools:
- firewalld-cmd
- firewalld-config
- firewalld-applet
```
system-config-firewall    firewall-config     firewall-cmd
    |                           |                |   
    |                           |                |  
iptables service         firewall daemoc & service
               |          |
               |          |
            iptables command
                    |
                    |
                kernel netfilter
```

# investigate the firewalld service state
> firewalld-cmd --state

# load the configuration into the firewall
> firewalld-cmd --list-all


# firewalld-cmd --permanent
only affects the configuration files, not the firewalld running in memory
## permanently remove the services from the configuration
> firewalld-cmd --permanent --delete-service={dhcpv6-client,mdns,smaba-client}
## permanently remove the dynamic ports
> firewalld-cmd --permanent --remove-port={1025-65535/udp,1025-65535/tcp}

# verify the configuration change
> firewalld-cmd --reload
