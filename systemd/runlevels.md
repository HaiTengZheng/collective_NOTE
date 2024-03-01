# runlevels
`/etc/inittab` (no longer used)
- halt mode
- single-user mode
- multi-user mode
- networked multiuser
- graphical ui
- reboot

# view current default target
> systemctl get-default

# set a default target
> systemctl set-default TARGET.target
`init $runlevel` (no longer used)

# runlevel map
> ls -l /usr/lib/systemd/system/*.target | grep runlevel
> systemctl list-unit-files *.target
```bash
.../runlevel0.target -> poweroff.target
.../runlevel1.target -> rescue.target
.../runlevel2.target -> multi-user.target
.../runlevel3.target -> multi-user.target
.../runlevel4.target -> multi-user.target
.../runlevel5.target -> graphical.target
.../runlevel6.target -> reboot.target
```
