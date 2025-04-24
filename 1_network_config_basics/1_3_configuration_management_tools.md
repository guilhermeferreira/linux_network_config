# Network Configuration Management Tools

Configuration management tools store network configuration information and apply it to the interfaces. These tools are:
- `ifupdown`.
- `NetworkManager`.
- `systemd-networkd`.

## ifupdown

Is a series of shell scripts to start (`ifup`) and stop (`ifdown`) network interfaces.

Widely used on legacy and embedded environments.

Read configuration from `/etc/network/interfaces` (Debian/Ubuntu) or `/etc/sysconfig/network-scripts` (Red Hat).

These scripts use either `ifconfig` or `ip` to apply changes.

## NetworkManager

Widely used on modern GUI environement (desktop distros).

Offers both graphical and command line configuration (`nmcli`) to manage connections.

It works with either `ifconfig` or `ip`.

## systemd-networkd

It is a module of `systemd`.

Widely used on command-line environments (server distros).

Provides tools such as `networkctl`.
