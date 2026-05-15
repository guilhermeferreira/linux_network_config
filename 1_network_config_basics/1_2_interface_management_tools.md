# Network Interface Management Tools

## Ethernet

There are two sets of Interface Management tools (i.e. packages) for Ethernet networks, `iproute` and `net-tools`.

### iproute / iproute2

The `iproute` is the most widely used Interface Management tool. It contains the commands:
- `ip` to control links, addresses, routes, and so one.
- `ss` to explore network sockets.

### net-tools

These tools are deprecated.
- `ifconfig` to configure the interfaces.
- `netstat` to explore network sockets.

## Wi-Fi

A Linux Wi-Fi interface is still a normal Linux network interface, so it uses the normal Ethernet/IP networking stack plus additional Wi-Fi-specific management layers.

In addition to the Ethernet management tools, Wi-Fi needs specific tools to manage its wireless characteristics.

### iw

The `iw` is the modern Interface Management tool for Wi-Fi.

### wireless-tools

This is the deprecated Wi-Fi package.
- `iwconfig` is used to display and change the parameters of the network interface.
- `iwlist` is used to scan for available wireless networks and display additional information about them.
