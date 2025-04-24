# Dynamic Host onfiguration Protocol (DHCP)

The most common tools are `dhclient` and `dhcpcd`.

## dhclient

| Command | Description |
|---------|-------------|
| `dhclient -v <iface>` | Acquire an address for the interface |
| `dhclient -r <iface>` | Release the address of the interface |

## dhcpcd

| Command | Description |
|---------|-------------|
| `systemctl status dhcpcd` | Display information about the daemon |
| `dhcpcd <iface>` | Acquire an address for an interface |
| `dhcpcd` | Acquire addresses for all interfaces |
| `dhcpcd -k <iface>` | Release the address of an interface |
| `dhcpcd -k` | Release addresses of all interfaces |
