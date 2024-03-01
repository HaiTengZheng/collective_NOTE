# Network Time Protol (NTP)

# Precision Time Protol (PTP)

# the `chrony` implement
- `chronyd` as daemon
- `chronyc` as the user interface
> /lib/systemd/system/chronyd.service
> /etc/chrony.conf
chrony is hardcoded to run under the non-privileged chrony accout

# systemd-timesyncd
