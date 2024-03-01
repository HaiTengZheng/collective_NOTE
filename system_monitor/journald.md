# journald logging system
part of the systemd ecosystem
> /etc/systemd/journald.conf
- journald is configured to store information in lots of smaller files
## disk-usage
> journalctl --disk-usage
## see the log entries form the current boot-up seesion
> journalctl -b
> journalctl -b -1
> journalctl --list-books
## -g
grep
> journalctl -g fail --case-sensitive=true
## the priority levels are the same as for the ryslog log messages
- 0 or emerg
- 1 or alert
- 2 or crit
- 3 or err
- 4 or warning
- 5 or notice
- 6 or info
- 7 or debug
> journalctl -p 0
> journalctl -p 3..3
## facilities
- auth
- authpriv
- cron
- daemon
- ftp
- kern
- lpr
- mail
- mark
- news
- syslog
- user
- uucp
- local0 though local7
> journalctl --facility uucp
> journalctl --facility=help
## other
the -S or --since specify time
> journalctl _UID=1000 -S today
output json format
> journalctl -u apache2 -o json
output pretty
> journalctl -u apache2 -o json-pretty
`--no-pager` allows you to pipe the journalctl output into another utility
## sealing
Forward Secure Sealing (FSS)
> sudo journalctl --setup-keys
- sealing key: `fss` in the same directory as the journalctl log files
- verification key: only appears as a text string on your screen
> sudo journalctl --veriy --veriy-key=verification_key
