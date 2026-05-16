# Wireless Management

Management tools apply configuration into the kernel. However, these configurations must be reapplied on every reboot.

Conventional management tools such as `ip` change IP, link, and routing. Wi-Fi management tools such as `iw` change Wi-Fi radio, mode, and channel.

## wireless-tools

`wireless-tools` is a legacy wireless management package equivalent to `net-tools`.

### Stack

These tools use the old kernel Wireless Extensions (`WEXT`) API.

### Commands

| Command       | Description |
|---------------|-------------|
| `iwlist <wlan-iface> scan` | Scan nearby wireless networks |
| `iwconfig <wlan-iface>`    | Display information about the connection |


## iw

[`iw`](https://wireless.docs.kernel.org/en/latest/en/users/documentation/iw.html) is the modern wireless management tool equivalent to `ip` (`iproute2`).

### Stack

This tool uses `cfg80211`/`nl80211`, which is a modern replacement for `WEXT`.

```
+--------------------------------------------------+
|                        iw                        |
|          Wi-Fi radio, mode, and channel          |
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

- `nl80211` is the userspace to kernel Wi-Fi API. It uses Netlink protocol.
- `cfg80211` is the kernel-side generic Wi-Fi framework. Drivers integrate into it.

### Commands

| Command | Description |
|---------|-------------|
| `iw dev <wlan-iface> scan` | Scan nearby wireless networks |
| `iw dev <wlan-iface> link` | Display information about the connection |
| `iw list`           | Display Wi-Fi capabilities |
| `iw event`          | Monitor events |
| `iw dev <wlan-iface> set power_save off` | Disable power save |
| `iw dev <wlan-iface> get power_save`     | Get power save |
| `iw dev <wlan-iface> station dump`       | Display stations connected to the AP |
