# Wi-Fi

Before setting up the IP address, we have to establish a wireless link. This is similar to plugging an Ethernet cable.

There are three set of tools:
- The `wireless-tools` package provides `iwconfig` and `iwlist`. However, it works only with WEP networks.
- The `wpa_supplicant` works with WPA2 networks.
- The `iwd` is more modern but not widely used yet.

## wireless-tools

| Command | Description |
|---------|-------------|
| `iwlist scan` | Scan nearby wireless networks |
| `iwconfig` | Display information about the connection |

## wpa_supplicant

| Command | Description |
|---------|-------------|
| `wpa_passphase <ESSID> > <file>.conf` | Save the password of a given network |
| `wpa_supplicant -i <wlan-iface> -c <file>.conf` | Connect to a given network |
| `wpa_supplicant -i <wlan-iface> -c <file>.conf -B` | Connect (on the `b`ackgound) to a given network |
