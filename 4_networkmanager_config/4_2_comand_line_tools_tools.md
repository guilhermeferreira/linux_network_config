# Using NetworkManager Command-Line Tools

NetworkManager provides one command-line interface, `nmcli`.

## nmcli

| Command | Description |
|---------|-------------|
| `nmcli` | Show connections [^1] |
| `nmcli connection` | Show the connections managed by NetworkManager |
| `nmcli device` | Show the connections organized by device |
| `nmcli connection show <profile>` | Show detailed info about a connection |
| `nmcli connection up <profile>` | Enable the connection |
| `nmcli connection down <profile>` | Disable the connection |
| `nmcli connection edit <profile>` | Edit the connection |

[^1]: A connection is a set of configurations for a network interface. It is called "profile" on the GUI. A connection is a collection of settings that can be applied to a device.

```
$ nmcli connection edit <profile>
nmcli> print connection
nmcli> set connection.id NewProfileName
nmcli> print ipv4
```
