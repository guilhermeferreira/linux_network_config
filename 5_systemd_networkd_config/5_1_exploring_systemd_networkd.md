# Using systemd-networkd

`systemd-networkd` is a configuration manager.

## Configuration files

Configuration files are named following the pattern `<number>-<iface>.network` (e.g. `10-enp1s0.network`).

### Locations

If we use only `systemd-networkd` to manage the network, files are in `/etc/systemd/network`, `/lib/systemd/network/`, or `/usr/lib/systemd/network/`.

If we use other software (e.g. Netplan) in conjunction with `systemd-networkd`, then files are in `/run/systemd/network`.

### Types

`systemd-networkd` splits networking into three layers of responsibility, each represented by a different file type:

- `.netdev` creates virtual network interface.
- `.link` configures an existing network interface on layer-2.
- `.network` configures an existing network interface on layer-3.

#### `.netdev`

This file type can create [virtual netowrk interfaces](https://developers.redhat.com/articles/2026/04/03/introduction-to-linux-interfaces-for-virtual-networking) such as:

- **Bridge**. A layer-2 virtual interface that acts like a virtual Ethernet switch, forwarding Ethernet frames between interfaces based on MAC addresses.
  ```
  [NetDev]
  Name=br0
  Kind=bridge
  ```
- **Bond**. A layer-2 virtual interface that combines multiple physical NICs into one logical interface.
  ```
  [NetDev]
  Name=bond0
  Kind=bond
  ```
- **Team**. A modern version of Bond interface, combining multiple physical NICs into one logical interface.
- **MACVLAN**. A layer-2 interface that splits one physical NIC into multiple logical NICs, leting multiple virtual interfaces share the same physical NIC.
- **VLAN**. A layer-2 virtual interface creates a tagged Ethernet subinterface, inserting a VLAN ID into Ethernet frames.
  ```
  [NetDev]
  Name=eth0.10
  Kind=vlan

  [VLAN]
  Id=10
  ```
- **VETH**. A layer-2 interface pair that acts like a virtual Ethernet cable.
- **VXLAN**. A layer-3 virtual interface that encapsulates Ethernet frames inside UDP packets.
- **GRE tunnel**. A layer-3 virtual interface that creates a generic Layer-3 tunnel.
- **WireGuard**. A layer-3 virtual interface that creates an encrypted VPN interface, where packets are encrypted, sent over UDP, and decrypted on the other side.
  ```
  [NetDev]
  Name=wg0
  Kind=wireguard
  ```
- **TUN**. A layer-3 virtual interface that connects IP packets to userspace programs.
- **TAP**. A layer-2 virtual interface that connects Ethernet frames to userspace programs.
- **Dummy**. A layer-3 interface that creates a fake NIC that goes nowhere.

#### `.link`

This file type modifies properties of a network interface before networking is configured. For example:

- Rename interfaces
  ```
  [Match]
  MACAddress=00:0a:35:24:97:ca

  [Link]
  Name=lan0
  MTUBytes=9000
  ```
- Set MTU
- Set MAC address
- Wake-on-LAN
- Offloading features

#### `.network`

Applies layer-3 networking to physical interfaces and/or virtual interfaces created by `.netdev`.

The `Match` section specifies to which interface is configured.
- Interface name
  ```
  [Match]
  Name=eth0
  ```
- MAC address
  ```
  [Match]
  MACAddress=aa:bb:cc:dd:ee:ff
  ```

Typical responsibilities include:
- IP addresses
  ```
  [Network]
  Address=192.168.1.10/24
  ```
- DHCP
  ```
  [Network]
  DHCP=yes
  ```
- DNS
  ```
  [Network]
  DNS=1.1.1.1
  ```
- Bridge membership
  ```
  [Network]
  Bridge=br0
  ```
- VLAN attachment
  ```
  [Network]
  VLAN=eth0.10
  ```
- Routes
  ```
  [Network]
  Address=192.168.1.10/24
  Gateway=192.168.1.254

  [Route]
  Destination=0.0.0.0/0
  Gateway=192.168.1.254

  [Route]
  Destination=192.168.2.0/24
  Gateway=192.168.1.254
  ```


## Tools

| Command | Description |
|---------|-------------|
| `networkctl` | Show all interfaces managed by systemd-networkd |
| `networkctl status` | Show the status of all interfaces managed by systemd-networkd |
| `networkctl status <iface>` | Show the status of a single interface managed by systemd-networkd |
