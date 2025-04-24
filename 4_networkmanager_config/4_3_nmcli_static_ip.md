# Configure static client using nmcli

```
$ nmcli connection down <profile>
$ nmcli connection edit <profile>
nmcli> set ipv4.method manual
nmcli> set ipv4.addresses 10.0.1.142/24
nmcli> set ipv4.gateway 10.0.1.1
nmcli> set ipv4.dns 10.0.1.1
nmcli> verify
nmcli> save
nmcli> quit
$ nmcli connection up <profile>
```
