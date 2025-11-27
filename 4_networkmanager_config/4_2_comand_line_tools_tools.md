# Using NetworkManager Command-Line Tools

NetworkManager provides one command-line interface, `nmcli`.

## nmcli

| Command | Description |
|---------|-------------|
| `nmcli` | Show connections [^1] |
| `nmcli connection` | Show the connections managed by NetworkManager |
| `nmcli connection show <profile>` | Show detailed info about a connection |
| `nmcli connection up <profile>` | Enable the connection |
| `nmcli connection down <profile>` | Disable the connection |
| `nmcli connection edit <profile>` | Edit the connection |
| `nmcli connection modify <profile>` | Modify a property from a profile |
| `nmcli device` | Show the connections organized by network interface |
| `nmcli device show <ifname>` | Show detailed info about a network interface |
| `nmcli device up <ifname>` | Enable the network interface |
| `nmcli device down <ifname>` | Disable the network interface |
| `nmcli device modify <ifname> [+/-]<setting>.<property> <value>` | Modify a property from a network interface |

[^1]: A connection is a set of configurations for a network interface. It is called "profile" on the GUI. A connection is a collection of settings that can be applied to a device.

### Configuring a Profile (connection)

```
$ nmcli connection edit "<profile>"
nmcli> print connection
nmcli> set connection.id NewProfileName
nmcli> print ipv4
```

### Configuring a Network Interface (device) 

Change the IP address:

```
$ nmcli device modify <iface> ipv4.address "192.168.11.77/24"
```

Add a route:

```
$ nmcli device modify <iface> +ipv4.routes "192.168.22.0/24 192.168.11.200 100"
```

See which profile manages a given device:

```
$ nmcli -t -f GENERAL.CONNECTION device show <iface>
GENERAL.CONNECTION:Wired connection 1
```

Display the properties of a device:

```
$ nmcli device show <iface>
```
