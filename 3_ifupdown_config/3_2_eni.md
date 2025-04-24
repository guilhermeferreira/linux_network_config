# Configuring systems using ENI

These configuration files are present in `/etc/network/interfaces`, hence the name ENI.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
    hostname mypc

auto eth1
iface eth1 inet static
    address 10.0.1.140/24
    gateway 10.0.1.1
    dns 10.0.1.1
    hostname mypc
```
