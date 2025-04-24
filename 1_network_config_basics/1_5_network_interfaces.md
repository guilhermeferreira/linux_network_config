# Discovering Network Interfaces

`udev` is responsible for recognizing network hardware and making it available to the system.

It makes the naming predictable.

## Common Interface Name Parts

| Prefix | Description     |
|--------|-----------------|
| `en`   | Ethernet (LAN)  |
| `wl`   | Wi-Fi (WLAN)    |
| `ww`   | Cellualr (WWAN) |

- `enp0s3` = Ethernet adapter on PCI bus 0, slot 3.
- `eno1` = Onboard Ethernet adapter 1.
- `wlx00c2c6bfc904` = Wi-Fi adapter identified by MAC `00:c2:c6:bf:c9:04`.

## Network Hardware Tools

- `lspci` = PCI devices.
- `lsusb` = USB devices.
- `lshw` = system hardware.
- `ethtool` = Ethernet adapters.
