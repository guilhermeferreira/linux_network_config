# Configuring Netplan

| Command | Action |
|---------|--------|
| `netplan try` | check if the configuration is good |
| `netplan apply` | Applies the configuration |

## Dynamic address

The file `/etc/netplan/00-enp0s1.yaml` uses NetworkManager and the renderer and DHCP.

```yaml
network:
  renderer: NetworkManager
  ethernets:
    enp0s1:
      dhcp4: true
  version: 2
```

## Static address

The file `/etc/netplan/00-enp0s2.yaml` uses `systemd-networkd` (the default renderer) and static IP:

```yaml
network:
  renderer: networkd
  ethernets:
    enp0s2:
      addresses: [10.10.0.2/24]
      gateway4: 10.10.0.1
      nameservers:
        addresses: [10.10.0.1]
  version: 2
```
