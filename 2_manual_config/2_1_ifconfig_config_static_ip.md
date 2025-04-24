# net-tools

`ifconfig` is part of the `net-tools` package, which was widely used but now is deprecated.

## ifconfig

| Command | Description |
|---------|-------------|
| `ifconfig` | Show active interfaces |
| `ifconfig -a` | Show all interfaces |
| `ifconfig <iface>` | Display information about an interface |
| `ifconfig <iface> up` | Make an interface active |
| `ifconfig <iface> <ipaddr>` | Assign an address to the interface |
| `ifconfig <iface> netmask <mask>` | Assign a network mask to the interface |

## route

| Command | Description |
|---------|-------------|
| `route add default gw <ipaddr>` | Add a default route |
