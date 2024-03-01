# /boot
On both BIOS-based and EFI/UEFI-based machines, the Linux kernel and the
`initramfs` files get installed in the `/boot` partition.

# On a BIOS-based machine
the `/boot` partition is `/dev/sda1`
> mount | grep 'boot'
- RHEL-type -> xfs
- Ununtu    -> ext4
The MBR is just the first 512 bytes of the drive.
## grub2.cfg
> /boot/grub2
The GRUB2 configuration file
- RHEL-type -> `/etc/grub.cfg` symbolic link points to the actual configuration
                file (`/boot/grub2/grub.cfg`)
## reconfigure
never edit the `grub.cfg` file, edit
> /etc/default/grub
then, rebuild grub.cfg by doing
> sudo grub2-mkconfig -o /boot/grub2/grub.cfg

# entries and BLS
The configuration files for menu choices, known as `BootLoaderSpec(BLS)` file
> /boot/loader/entries
- Whenever you boot your machine, GRUB2 will take information from these BLS
  files and use it to populate the boot menu.
- A new BLS file will be generated automatically every time a new linux kernel
  is installed, even if it's kernel that you've compiled yourself.
- If you do a system update and dnf removes any older kernels, the BLS files 
  for those older kernels will be deleted.

the variable pulled in the `/boot/grub2/grub.cfg` and the `/boot/grub2/grubenv`



# GRUB2 on EFI/UEFI-based machine
- `/boot` is mounted on `/dev/sda2`
- `/boot/efi` is mounted on `dev/sda1`
The `/boot/efi` is where the bootloaders reside. It must formatted with the 
`vfat` filesystem, because nothing else works.
## gurb2-efi.cfg
link to `/boot/grub2/grub2.cfg`
## /boot/efi/EFI/BOOT
The `BOOTX64.EFI` file is part of the `shim` system, which allows Linux to boot
on machines that have the Secure Boot feature enabled.

The `fbx64.efi` file is the fallback bootloader, its job is to recreate the boot
manager options that are built into the firmware in case they somehow get deleted.
It does this by scanning the `BOOT64.csv` files that are in the subdirectories 
for any operating systems that are installed.
## /boot/efi/EFI/fedora (or other system name)
- grubx64.efi:  This is what GRUB2 works on an EFI/UEFI machine.
- shim64.efi:   Go alone with the BOOTX64.CSV to make fedora work on Secure Boot
                machine
- mmx64.efi:    It is part of the `Machine Owner Key system`, which also helps
                out with Secure Boot.
- BOOTX64.CSV:  works with the fallback bootloader and contains a boot menu entry
                for this installation of fedora
                It `UTF-16` Unicode file
