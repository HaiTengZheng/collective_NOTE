# syslog
> RFC 5424
a logging standard for a range of sources, from the kernel to daemons to user
space

# high-level format
- PRI   the message facility/serverity
- VER   the syslog protocol number (usually left out since it can only be 1)
- TS    contains the time when the message was generated using ISO 8601 format
- HN    identifies the machine that sent the message
- APP   identifies the application (or a device) that sent the message
- PID   identifies the process that sent the message
- MID   an optional message ID

# syslog binary
- syslog-ng
- rsyslog       extends the syslog protocol and can also be used with systemd

# rsyslog service
> sudo dnf install rsyslog
- store log file in plaintext format
- no built-in way to stucture the view of rsyslog log files
## levels
0. emerg, panic(Emergency)
1. alert(Alerts)
2. crit(Critical)
3. err(Errors)
4. warn(Warinings)
5. notice(Notification)
6. info(Infomation)
7. debug(Debugging)
## /etc/rsyslog.conf
```sh
# Provides UDP syslog reception
# for parameters see http://www.rsyslog.com/doc/imudp.html
module(load="imudp") # needs to be done just once
input(type="imudp" port="514")

# Provides TCP syslog reception
# for parameters see http://www.rsyslog.com/doc/imtcp.html
#module(load="imtcp") # needs to be done just once
#input(type="imtcp" port="514")
```
