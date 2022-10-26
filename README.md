# Debian11BeowulfGuide Bullseye


Install necessary services
```
apt install tftpd-hpa isc-dhcp-server debootstrap nfs-kernel-server net-tools
mkdir /pxeroot
  
cd /pxeroot
  
debootstrap bullseye /pxeroot

```
Edit fstab inside of chroot
```
#/etc/fstab: static file system information.
# <file system>   <mount point>   <type>   <options>   <dump>    <pass>
/dev/ram0  /       ext2   defaults    0   0
proc       /proc      proc   defaults    0   1
tmpfs      /tmp       tmpfs  defaults    0   1
```
Install packages needed inside chroot
```

apt install linux-image-amd64


```
Leave Chrooot

```
exit
```

edit /etc/dhcpd/dhcpd.conf

```

subnet 192.168.100.0 netmask 255.255.255.0 {
    range 192.168.100.100 192.168.100.200;
    option subnet-mask 255.255.255.0;
    filename "pxelinux.0";
    next-server 192.168.100.1;
    option root-path "192.168.100.1:/pxeroot";
    option broadcast-address 192.168.100.255;
}

```
set static ip on interface which you will be serving ip to nodes (you will want to make this permanent, but for now)

```

ifconfig enp0s8 192.168.100.1

```

run dhcpd

```
dhcpd
```


edit /etc/default/tftpd-hpa

```


```
