# Configure static client using nmcli

## Profile (connection)

```
$ nmcli connection down "<profile>"
$ nmcli connection edit "<profile>"
nmcli> set ipv4.method manual
nmcli> set ipv4.addresses 10.0.1.142/24
nmcli> set ipv4.gateway 10.0.1.1
nmcli> set ipv4.dns 10.0.1.1
nmcli> verify
nmcli> save
nmcli> quit
$ nmcli connection up "<profile>"
```

```
$ nmcli connection modify "<profile>" +ipv4.routes "192.168.11.0/24 192.168.22.200 100"
```

## Network Interface (device)

```
$ nmcli device modify <iface> +ipv4.routes "192.168.11.0/24 192.168.22.200 100"
```

