# Wireless Authentication

These tools manage authentication and association.

## wpa_supplicant

[`wpa_supplicant`](https://wireless.docs.kernel.org/en/latest/en/users/documentation/wpa_supplicant.html) is the authentication tool for Stations.

Responsibilities:
- Scan networks.
- Authenticate.
- Associate.
- WPA2/WPA3 handshake.
- Roaming.
- PMK/PTK negotiation.

### Stack

This tool uses `cfg80211`/`nl80211`.

```
+--------------------------------------------------+
|                  wpa_supplicant                  |
|   WPA2/WPA3 auth, association, roaming, RSN      |
+--------------------------------------------------+
|                     nl80211                      |
|       Generic Linux userspace Wi-Fi API          |
+--------------------------------------------------+
|                    cfg80211                      |
|      Kernel Wi-Fi framework/regulatory core      |
+--------------------------------------------------+
|                   Wi-Fi driver                   |
+--------------------------------------------------+
|             Wi-Fi firmware/hardware              |
+--------------------------------------------------+
```

### Commands

| Command | Description |
|---------|-------------|
| `wpa_passphase <ESSID> > <file>.conf` | Save the password of a given network |
| `wpa_supplicant -i <wlan-iface> -c <file>.conf` | Connect to a given network |
| `wpa_supplicant -i <wlan-iface> -c <file>.conf -B` | Connect (on the `b`ackgound) to a given network |

### Configuration

Add the file `/etc/wpa_supplicant/wpa_supplicant-wlan0.conf` for interface-specific WPA supplicant configuration.

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
update_config=1

network={
    ssid="MyNetwork"
    psk="mypassword"
}
```

Enable the interface-specific WPA supplicant service.

```
systemctl enable wpa_supplicant@wlan0
```

## hostapd

[`hostapd`](https://wireless.docs.kernel.org/en/latest/en/users/documentation/hostapd.html) is the authentication tool for Access Points.

Responsibilities:
- Create beacons.
- Advertise SSID.
- Authenticate stations.
- Manage WPA handshakes.
- Maintain station table.

### Stack

It also uses `cfg80211`/`nl80211`.

```
+--------------------------------------------------+
|                      hostapd                     |
|       Beaconing, WPA auth, AP management         |
+--------------------------------------------------+
|                     nl80211                      |
|       Generic Linux userspace Wi-Fi API          |
+--------------------------------------------------+
|                    cfg80211                      |
|      Kernel Wi-Fi framework/regulatory core      |
+--------------------------------------------------+
|                   Wi-Fi driver                   |
+--------------------------------------------------+
|             Wi-Fi firmware/hardware              |
+--------------------------------------------------+
```

### Configuration

Create the `/etc/hostapd/hostapd.conf` file. The example bellow is for 802.11n (Wi-Fi 4).

```
interface=wlan0
driver=nl80211
ssid=MyNetwork
hw_mode=g
channel=6
ieee80211n=1
wmm_enabled=1
ht_capab=[HT20][SHORT-GI-20]
auth_algs=1
wpa=2
wpa_passphrase=mypassword
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
```

Add the following line to the `/etc/default/hostapd` file to tell the `hostapd` where to find the configuration.

```
DAEMON_CONF="/etc/hostapd/hostapd.conf"
```

Start the service.

```
sudo systemctl start hostapd
```

Check connected stations.

```
iw dev wlan0 station dump
```
