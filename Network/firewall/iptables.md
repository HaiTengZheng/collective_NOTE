# iptables  (old tool)
build a `Netfilter` firewall
> iptables <option> <chain> <matching criteria> <target>
- the list of rules is processed sequentially from top to bottom
## list all rules in a chain
> iptables -L -v


-------------------------------------------------------------------------------
# three default tables
- Filter
- NAT
- Mangle

## Filter
### three default chains
- Input
- Forword
- Output

-------------------------------------------------------------------------------
# three main actions
- ACCEPT
- DROP
- RETURE

-------------------------------------------------------------------------------
# -A
add a rule to a chain
- -I        interface
- -P        protocol
- -s        source
- -dport    destination port
- -j        target
e.g.
> iptables -A INPUT -i ens33 -p tcp -s 1.2.3.0/24 --dport 22 -j ACCEPT

# -D 
delete a rule

# -j LOG
log a rule
