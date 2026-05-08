# Introduction

## Motivation

Desktop Linux use **NetworkManager**, which is heavy and desktop-focused (D-Bus + GUI expectations). However, embedded systems needed:
- Fast boot.
- Small footprint.
- Simple API.
- Headless operation

ConnMan was built to be:
- Lightweight.
- Event-driven.
- Easy to integrate into firmware images (Yocto, Buildroot).

ConnMan is a high-level network manager that:
- Detects interfaces (Ethernet, Wi-Fi, etc.)
- Decides how they should be configured (DHCP, static, etc.)
- Applies configuration using either Netlink (directly), or helpers such as `systemd-networkd`.

## Operation

ConnMan is an active daemon network manager that:
- Runs continuously.
- Makes decisions (DHCP vs static, connect/disconnect).
- Applies configuration.
- Stores state.
- Reacts to events (cable plugged, Wi-Fi appears).

## Commands

```
$ connmanctl services
*AR Wired                ethernet_1007236ec75c_cable
*AR Wired                ethernet_1007236ec759_cable
```

Meaning:
- `A` = autoconnect.
- `R` = ready.
- `ethernet_1007236ec759_cable` = **Technology** + **ID** (e.g. MAC for Ethernet) + **Connection Type**.

## Configuration

The configuration files are in `/var/lib/connman/`:

```
drwx------ 2 root root 4096 Feb 27 21:08 ethernet_1007236ec759_cable
drwx------ 2 root root 4096 Feb 27 21:05 ethernet_1007236ec75c_cable
-rw------- 1 root root   84 Feb 27 17:26 settings
```
