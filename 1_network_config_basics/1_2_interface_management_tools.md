# Network Interface Management Tools

There are two types of network tools in Linux:
- Interface managment tools are the ones that apply configuration into the kernel. However, these configurations must be reapplied on every reboot.
- Configuration management tools are the tools that store settings and apply them.

There are two sets of Interface Managment tools, `iproute` and `net-tools`.

## iproute / iproute2

The `iproute` is the most widely used Interface Management tool. It contains the commands:
- `ip` to control links, addresses, routes, and so one.
- `ss` to explore network sockets.

## net-tools

These tools are deprecated.
- `ifconfig` to configure the interfaces.
- `netstat` to explore network sockets.
