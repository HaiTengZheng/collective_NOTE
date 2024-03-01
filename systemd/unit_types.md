# service
> .service
the configuration files for services
- replave the System V fashinoed init scripts

# socket
> .socket
an inter-process communcation socket
- enable communcation between different system services
- automatically wake up a sleeping service when it receives a connection 
    request

# slice
> .slice
are used when configuring `cgroups`, defines a group of hierarchical units that
    manage system process

# mount and automount
> .mount
> .automount
contain mount point information for filesystems that are controlled by systemd
- normally get created automatically

# target
are used during system startup, for grouping units and for providing well-known
    synchronization points

# timer
> .timer
for scheduling jobs that run on a schedule
- replace the old `cron` system

# path
> .path
for services that can be started via path-based activation

# swap
> .swap
contain information about your swap partitions

# scope
> .scope
an externally created process

# device
> .device
defines a device file recognized by the kernel


