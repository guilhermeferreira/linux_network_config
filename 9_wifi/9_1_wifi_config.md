# Wi-Fi

A Linux Wi-Fi interface is still a normal Linux network interface, so it uses the normal Ethernet/IP networking stack such as `ip` and `ifconfig`. Plus, there are management tools to control the Wi-Fi specific aspects of the interface.

```
Wi-Fi = Ethernet-like networking
      + Wireless radio management
      + 802.11 authentication/association
```

There are three set of tools:
- Interface Management
   - The deprecated `net-tools` package.
   - The modern `iproute2` package.
- Wireless Management
   - The `wireless-tools` package provides `iwconfig` and `iwlist`. However, it works only with WEP networks.
   - The `iw` tool is the Wi-Fi version of the `ip` command.
- Wireless Authentication
   - The `wpa_supplicant` is the Station authentication tool for WPA/WPA2/WPA3 networks.
   - The `hostapd` is the Access Point authentication tool. 
   - The `iwd` (**i**Net **W**ireless **D**aemon) is more modern (but not widely used yet) wireless daemon intended to replace both `iw` and `wpa_supplicant`.

Before setting up the IP address, we have to establish a wireless link. This is similar to plugging an Ethernet cable.

## Interface Management

These tools manage the Ethernet-like aspects of the Wi-Fi interface. For example, enable the interface:

```
ip link set wlan0 up
```

## Wireless Management

The Wireless Management tools manage the radio. For example, to scan Wi-Fi networks.

They manage:
- Radio.
- Channels.
- Modes.
- Topology such as mesh/ad-hoc/AP.

There are two set of tools:
- `wireless-tools` (deprecated).
- `iw`.

## Wireless Authentication

These tools authenticate and associate. They perform:
- WPA/WPA2/WPA3 authentication.
- Key exchange.
- Association to SSID.
- Roaming.

There are two tools:
- `wpa_supplicant` for Stations.
- `hostapd` for Access Points.
