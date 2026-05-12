# Configuring systemd-networkd

The two most important sections are:
- `[Match]` indicates which interface to configure.
- `[Network]` indicates the settings to apply.

## Static address

Create a file `/etc/systemd/network/20-static.network`:

```
[Match]
Name=eth1

[Network]
Address=10.10.1.20/24
Gateway=10.10.1.1
DNS=10.10.1.1
```

Restart the service to apply the configuration.

```
sudo systemctl restart systemd-networkd
```

## Dynamic address

Create a file `/etc/systemd/network/10-dynamic.network`:

```
[Match]
Name=eth1

[Network]
DHCP=yes
```

Restart the service to apply the configuration.

```
sudo systemctl restart systemd-networkd
```

When `DHCP=yes`, `systemd-networkd` will:

1. send `DHCPDISCOVER`
2. receive `DHCPOFFER`
3. send `DHCPREQUEST`
4. receive `DHCPACK`
5. configure:
   - IP address
   - routes
   - DNS (via `systemd-resolved` if used)

### renew

The command

```
sudo networkctl renew eth1
```

makes the client execute a subset of the DHCP messages:

1. send `DHCPREQUEST`
2. receive `DHCPACK`

### reconfigure

The command

```
sudo networkctl reconfigure eth1
```

makes the client execute the entire DHCP flow:

1. send `DHCPRELEASE`
2. send `DHCPDISCOVER`
3. receive `DHCPOFFER`
4. send `DHCPREQUEST`
5. receive `DHCPACK`
6. configure:
   - IP address
   - routes
   - DNS (via `systemd-resolved` if used)
