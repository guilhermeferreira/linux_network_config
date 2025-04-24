# Domain Name System (DNS)

There are two primary ways to configure DNS on a Linux system: **static** and **dynamic**. In a **static DNS configuration**, you manually define DNS entries that do not change unless you edit them directly. This includes adding entries to `/etc/hosts` for hostname-to-IP mapping or setting a fixed nameserver in `/etc/resolv.conf`.

On the other hand, a **dynamic DNS configuration** is automatically managed by services like NetworkManager, `systemd-resolved`, or DHCP clients. These tools update DNS settings based on the current network environment, often rewriting `/etc/resolv.conf` with nameservers received from the network.

## Static Configuration

The system resolver library (e.g., glibc) uses it before querying DNS.

### Files

#### `/etc/hosts`

A static, local file that maps hostnames to IP addresses.

```
127.0.0.1    localhost
10.10.0.1    meet.jitsi.com
```

## Dynamic Configuration

### Files

The system resolver library uses these files when it needs to contact DNS servers.

#### `/etc/resolv.conf`

The file `/etc/resolv.conf` has the DNS server addresses.

If the `/etc/hosts` doesn’t resolve. The following tools use the `/etc/resolv.conf` to find a resolver server:
- `nslookup`.
- `dig`.
- `ping`.
- `ssh`.

It is updated by:
- NetworkManager.
- `systemd-resolved`.
- DHCP client (e.g., `dhclient`).

#### `/etc/systemd/resolved.conf`

The file `/etc/systemd/resolved.conf` is managed by `systemd-resolved`, which is a `systemd` service that provides network name resolution to local applications.

### Servers

Some DNS servers are:

#### Cludflare

```
nameserver 1.1.1.1
```

#### Google

```
nameserver 8.8.8.8
```

#### Quad9

```
nameserver 9.9.9.9
```
