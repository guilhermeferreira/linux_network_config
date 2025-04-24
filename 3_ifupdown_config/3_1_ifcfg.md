# Configuring systems using ifcfg

These configuration files are present in `/etc/sysconfig/network-scripts`.

## ifcfg file

Each interface has an `ifcfg` configuration file such as `ifcfg-eth0`:

```
DEVICE=eth0
HWADDR=08:00:04:BF:56:80 
ONBOOT=yes
BOOTPROTO=dhcp
```

## ifdup script

```
ifup eth0
```

## ifdown script

```
ifdown eth0
```
