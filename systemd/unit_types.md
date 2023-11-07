# service
the configuration files for services
- replave the System V fashinoed init scripts

# socket
- enable communcation between different system services
- automatically wake up a sleeping service when it receives a connection 
    request

# slice
are used when configuring `cgroups`

# mount and automount
contain mount point information for filesystems that are controlled by systemd
- normally get created automatically

# target
are used during system startup, for grouping units and for providing well-known
    synchronization points

# timer
for scheduling jobs that run on a schedule
- replace the old `cron` system

# path
for services that can be started via path-based activation

# swap
contain information about your swap partitions

