# check 
> egrep --color "vmx|svm" /proc/cpuinfo
- vmx -> Intel processors
- svm -> AMD processors

# install
main: QEMU, libvirt, oVirt
- qemu-kvm
- qemu-img
- libvirt
- libvirt-client
- virt-manager
- virt-install
- virt-viewer
> sudo dnf groupinfo virtualization
> sudo dnf install @virtualization
> sudo systemctl start libvirtd
> sudo systemctl enable libvirtd

# add the IOMMU configuration
> /etc/default/grub
find the `GRUB_CMDLINE_LINUX`
> intel_iommu=on
# check
- check whether our host is compatible with all the necessary KVM requirement
> virt-host-validate
- check whether our virtualization host has a correctly configured default 
  virtual network switch/bridge
> virsh net-list
- check whether we have any virtual machines running
> virsh list

# important
- the overall KVM stack is built as a module

