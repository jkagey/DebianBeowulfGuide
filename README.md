# Debian11BeowulfGuide Bullseye



> apt install tftpd-hpa isc-dhcp-server debootstrap nfs-kernel-server

> mkdir /pxeroot
  
> cd /pxeroot
  
> debootstrap bullseye /pxeroot

># /etc/fstab: static file system information.
># <file system>   <mount point>   <type>   <options>   <dump>    <pass>
>/dev/ram0  /       ext2   defaults    0   0
>proc       /proc      proc   defaults    0   1
>tmpfs      /tmp       tmpfs  defaults    0   1
