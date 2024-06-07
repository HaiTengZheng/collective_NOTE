# journalctl
system use `systemd`

# -n
number of journal entries to show


# following active logs for a unit
> journalctl -fu unitname
## -f
stand for `follow`
## -u
unit

# filter by time
> journalctl --since "2021-01-01 00:00:00"
> journalctl --until today
> journalctl --since "2021-01-01 00:00:00" --until today

# filter for a specific log level
> journalctl -p log_level
- emerg
- alert
- crit
- err
- warning
- notice
- info
- debug

# see logs from a previous boot of the system
> journalctl --list-boots
> journalctl -b 2

# kernel message
> journalctl --K
> journalctl --dmesg
