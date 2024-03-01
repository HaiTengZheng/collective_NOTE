# man page
> systemd.resource-control

# global setting file location
> /sys/fs/cgroup

# system.slice/

# user.clice/
set at the user slice level
- Each of these user slice subdirectories contains attribute files for all
  the resource controllers
- All the applicable settings for a particular user would be contained in
  the user slice directory for that user

# options
- MemoryMax
- MemoryHigh
- MemoryLow
- MemoryMin
...
