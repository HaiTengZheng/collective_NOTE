# the `sysstat` package
take the raw data from the kernel counters and allows you to display and store
the metrics and historical process running database
> sudo dnf install sysstat

# journalctl
> journalctl --since "3 hour ago"
> journalctl --since "3 hour ago" --until "2021-09-26 18:30:00"
> journalctl -f
> journalctl -f -u apparmor.service
## -o (--output)

# uptime

# free -h

# vmstat
> vmstat --unit M 1

# time

# iostat
monitor I/O devices (output edited)

# ss
> ss -atup
dump socket statistics

# netstat
an outdated way to gather and display interface stats

# lsof
> lsop -p 3233

# sar
collects, report, and store system activity

# perf

# mpstat

# pidstat

# cifsiostat
report statistics about shared filesystems, printers, or network serial ports

# ps
## list the processes with the highest CPU usage
> ps ax --format pid,%cpu,cmd --sort -%cpu
##
> ps axo pid,pri,rtprio,ni,cls,comm 

# chrt
display the scheduling policy and priority of the web server processes
> chrt -p [PID]
