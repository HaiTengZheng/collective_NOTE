# made of three Linux kernel primitives
- Namespaces
- Control groups (cgroups)
- Layered file systems or rootfs

# cgroups
Control groups allow resources to be controlled and accounted for based on
process groups.
- Cgroups provide a mechanism to aggregate sets of tasks or processes and their
  future children into hierarchical groups
## Cgroups are listed with the pseudo filesystem subsystem
> /sys/fs/cgroup

# Namespaces
A Namespace provide an abstraction to a global system resourc that will appear
to the processes within the defined namespace as its own isolated instance of a
specific global resource.
- The Filesystem Mount Namespace (mnt)
- The UTS Namespace
- The IPC Namespace (ipc)
- The Network Namespace
- The User and Group ID Namespace
- Security Modules and Namespace
- The Security Keys Namespace
- The Device Namespace
- The Time Namespace
Namespaces are used to implement containers, they provide the required isolation
between a container and the host system.
