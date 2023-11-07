# configure files
> /etc/systemd
> ls -l *.conf
- on Fedora, `resolved` `timesyncd` `networkd` are all disabled. 

## remark: comment lines
all of these configuration files line is commented out, which means that
    these are the default parameters that are compiled in. To change something,
    you would uncomment the line for disired parameters and change its value.

## remark: find in man page
you have to add `systemd-` test string to the front of the filename to find its
    man page
e.g.
> man systemd-system.conf

## timesyncd.conf
for service that synchronizes the machine's time to a trusted external source
- RHEL distros use an alternate time-synchronization service called `chronyd`
- Fedora use `chronyd` for time-keeping, but it still has the `timesyncd`
    component

## system.conf
set the configuration for the `systemd init` process

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# the systemd unit files
## the default location for unit files
> /lib/systemd/system/
either come with the operating system or come with any packages that you might
    install

## modify or create unit files
> /etc/systemd/system/
any unit files in this directory that have the same name as unit files in 
    /lib/systemd/system/ take precedence

## remark: read unit files
> man systemd.unit

## remark: look up a specific directive
> man systemd.directives
