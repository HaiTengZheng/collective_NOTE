# shortcut
## poweroff shortcut
> Ctrl-Alt-Delete

On Linux systems that do not use systemd, it is contolled by the 
    `/etc/iniitab' (no longer use in other system)

## configure `Ctrl-Alt-Delete` in the Linux Console
> man 7 systemd.special
The `Ctrl-Alt-Delete` unit file is not a service, but a target, so it does not
    run as a daemon. If the `/etc/systemd/system/ctrl-alt-del.target` symlink
    exists, `Ctrl-Alt-Delete` is enables.

> sudo systemctl diable ctrl-alt-del.target
removed

> sudo systemctl mask ctrl-alt-del.target
link to /dev/null

> sudo systemctl unmask ctrl-alt-del.target
removed

> sudo systemctl enable ctrl-alt-del.target
link to /lib/systemd/system/reboot.target


-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# commands
In Linux distributions with systemd, the classic old commands are not installed
    on the system. Intead, their names are symlinked to the systemctl command.

e.g. use stat command found that
> stat /sbin/shutdown
- /sbin/shutdown -> ../bin/systemctl
- /sbin/halt -> ../bin/systemctl
- /sbin/poweroff -> ../bin/systemctl
- /sbin/reboot -> ../bin/systemctl

## shutdown
> shutdown -h now
shut down immediately, with no notification to other logged-in users

> shutdown -h +10
shut down in 10 minutes with notifications

> shutdown -c
cancel the shutdown

> shutdown -h +10 "own message"
create your own message

> shutdown -h 22:10
set a shutdown time in 24 hour format 'hh:mm' format

> shutdown -r
reboot

> shutdown -H
halt the system without powerinf off

> shutdown
with no options is equivalent to 'shutdown -h +1'

## halt
> man 8 halt

## poweroff
> man 8 poweroff

## reboot
> man 8 reboot

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# control with systemctl
> systemctl poweroff
> systemctl shutdown
> systemctl reboot
> systemctl halt

- man 8 systemd-poweroff.service
- man 8 systemd-halt.service
- man 8 systemd-reboot.service
- man 8 systemd-kexec.service

note:
    The systemctl shutdown commands do not have the many options that the
        legacy commands do, which does not matter all that much because there
        are a lot of redundant options in the legacy commands.

## power saving mode
systemctl provides power saving modes:
- suspend
- hibernate
- hybrid-sleep
- suspend-then-hiberate

Power management is affected by your UEFI, CPU capabilities, udev, Advanced
    Configuration and Power Interface (ACPI), kernel compilation options, and
    posssibly other devices and programs.

### suspend
> systemctl suspend
This stores your current seeion in RAM and puts all hardware into a suspended
    state.

### hibernate
> systemctl hibernate
This stores your seeion on disk and powers off the machine.
    
### hybrid-sleep
> systemctl hybrid-sleep
This suspends your system to both memory and disk, and shuts off all devices
    expect RAM.

### suspend-then-hibernate
> systemctl suspend-then-hibernate
First goes into suspend mode, then enters hibernation after the period of time
    specified by the `HibetnateDelaySec=` setting in `/etc/systemd/sleep.conf`

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# cron
> sudo dnf install cronie cronie-anacron
create scheduled in `/etc/crontab`
> man 8 cron
> man 1 crontab
> man 5 crontab

# rtcwake
stops and wakes your system, send it to ACPI

- system's real-time clock (RTC) should be set to Coordinated Universal Time
    (UTC)

- `/sys/power/state` include sleep states your system supports, on non-systemd
    system is `proc/acpi/info`

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# ACPI
## sleep states
- S0    System is running, monitor may be off, most periherals are on
- S1    Power-on suspended, CPU stops, power to CPU and RAM is on
- S2    CPU is powered off, dirty cache is flushed to RAM
- S3    Also called standby, sleep, and suspend-to-RAM. Data may not be written
            to disk
- S4    Hibernation, suspend-to-disk. Everything in RAM is written to disk and 
            system is powered down.

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# runlevel
> man runlevel
`/etc/inittab` (no longer used)
