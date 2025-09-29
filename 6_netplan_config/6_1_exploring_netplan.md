# Using Netplan

Netplan allows us to define network settings in a YAML file.

It is a manager of configuration managers. Which it calls renderer.

Configuration is store in `/etc/netplan`.

Create a YAML file for each interface.

Netplan doesn't configure the interfaces but delegates the task to a renderer.

## Renderers

A renderer is the software that applies the configuration.

Netplan can choose to work with either **NetworkManager** or **systemd-networkd**.

- **systemd-networkd** is a network management daemon that’s part of `systemd`.
It configures and manages network interfaces directly (IP addresses, routes,
DNS, VLANs, tunnels, bridges, etc.). It is lightweight, has minimal dependencies
and is very good for servers, embedded systems, or environments where you don’t
need Wi-Fi auto-discovery or user-friendly GUI tools.
Configs live in: `/etc/systemd/network/*.network`, `.netdev`, `.link`.

- **NetworkManager** is a more feature-rich network management daemon. It provides
dynamic and user-friendly control of network interfaces (especially Wi-Fi, VPNs,
and desktop use cases). It is great for laptops and desktops (handles Wi-Fi,
hotspots, roaming, VPNs).
Configs live in: `/etc/NetworkManager/NetworkManager.conf` and `/etc/NetworkManager/system-connections/`.
