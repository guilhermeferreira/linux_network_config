# Using Netplan

Netplan allows us to define network settings in a YAML file.

It is a manager of configuration managers.

Configuration is store in `/etc/netplan`.

Create a YAML file for each interface.

Netplan doesn't configure the interfaces but delegates the task to a renderer.

## Renderers

A renderer is the software that applies the configuration.

Netplan can choose to work with either **NetworkManager** or **systemd-networkd**.
