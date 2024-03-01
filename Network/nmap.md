# nmap (Network Mapper)
- Nping
- Ncrack
- Ncat
- Zenmap
- NSE

# finding online hosts
`ping scan` or `ping sweep`
> nmap -sn <target>
- `-sn` option disable port scanning, leaving only the host discovery phase
  enabled
- nmap takes as a target any option not recofnized and it supports IPv4/IPv6
  addressed, hostnames, and network ranges that can be defined using wildcards
  and Classes Inter-Domain Routing (CIDR) notation.
e.g.,
> nmap -sn 192.168.0.1/24
## tracing routes
> nmap -sn --traceroute google.com microsoft.com
- `--traceroute` trace the route from the scanning machine to the traget host
## running Nmap Scripting Engine (NSE) during host discovery
depend on the `hostrule` specified
e.g.,
> nmap -sn --script dns-brute websec.mx
- `--script` <file, folder, category>
> nmap -sn --script broadcast-ping 192.168.0.1/24
- `broadcast-ping`, which use a broadcast ping request to attempt to discover
  online hosts

# listing open ports on a target
> nmap scanme.nmap.org

# use a different DNS server
> nmap --dns-servers 8.8.8.8,8.8.4.4 scanme.nmap.org
- `--dns-servers` <serv [, serv2], ...>

# check whether the target is online
> nmap -Pn scanme.nmap.org
- `-n`, skip this step

