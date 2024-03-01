# NetworkManager
- uses plugins read and write this data
- uses the INI-key file format to store connection profile data
## files
> /etc/NetworkManager/system-conncetions
> /usr/lib/NetworkManager/system-conncetions
> /run/NetworkManager/system-conncetions

## connection files
contain the network configuration

## the `keyfile` plugin
- always remains active and stores any connection that no other active plugin
    support
- ignores file that could be read or written by any non-root user


# ref
> GNOME Developer Documentation


# Vendor ID (the 16-bit number of the vendor, the `VID`)
# Product ID (the 16-bit number of the product number, the `PID`)
> PCI:  lspci -nn
> USB:  lsusb
```bash
# identify the card
lspci | grep broadcom
## get the beginning information `00:00.0 ***`
# get the detailed device information
lspci -vv -s 00:00.0
# list the modules that were loaded in the kernel and search the identified
# chipest of the wireless card
lsmod | grep -i broadcom
# display the module information
modinfo broadcom
```
