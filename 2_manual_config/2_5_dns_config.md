# Domain Name System (DNS)

The file `/etc/resolv.conf` has the DNS server addresses.

The file `/etc/systemd/resolved.conf` is managed by `systemd-resolved`, which is a `systemd` service that provides network name resolution to local applications.

Some DNS servers are:

## Cludflare

```
nameserver 1.1.1.1
```

## Google

```
nameserver 8.8.8.8
```

## Quad9

```
nameserver 9.9.9.9
```
