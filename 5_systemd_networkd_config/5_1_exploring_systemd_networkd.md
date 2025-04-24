# Using systemd-networkd

`systemd-networkd` is a configuration manager.

## Configuration files

Configuration files are named following the pattern `<number>-<iface>.network` (e.g. `10-enp1s0.network`).
- If we use only `systemd-networkd` to manage the network, files are in `/etc/systemd/network`.
- If we use other software (e.g. Netplan) in conjunction with `systemd-networkd`, then files are in `/run/systemd/network`.

## Tools

| Command | Description |
|---------|-------------|
| `networkctl` | Show all interfaces managed by systemd-networkd |
| `networkctl status` | Show the status of all interfaces managed by systemd-networkd |
| `networkctl status <iface>` | Show the status of a single interface managed by systemd-networkd |
