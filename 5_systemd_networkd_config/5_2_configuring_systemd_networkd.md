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
