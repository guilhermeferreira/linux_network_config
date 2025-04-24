# Configuring a Network Connection

Network connect needs:
- An IP address in a valid range.
  - Static IP is manually set (`iproute` and `net-tools`).
  - Dynamic IP is set by DHCP (`dhclient` and `dhcpd`).
- A route to communicate with hosts outside the network.
- A DNS server address to resolve names to IP addresses.

## Private Network Ranges

These addresses do not exist on the Internet and are not routable.

| Address Range  | Available Addresses |
|----------------|---------------------|
| 10.0.0.0/8     | ~16,000,000         |
| 172.16.0.0/12  | ~65,000             |
| 192.168.0.0/16 | 254                 |

## Network Management Tools

There are two types of network tools in Linux:
- [Interface Management](1_network_config_basics/1_2_interface_management_tools.md) tools are the ones that apply configuration into the kernel. However, these configurations must be reapplied on every reboot.
  - `iproute`.
  - `net-tools`.
- [Configuration Management](1_network_config_basics/1_3_configuration_management_tools.md) tools are the tools that store settings and apply them.
  - `ifup`/`ifdown`.
  - NetworkManager.
  - `systemd-networkd`.
