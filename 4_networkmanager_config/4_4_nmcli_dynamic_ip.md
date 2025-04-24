# Configure dynamic client using nmcli

```
$ nmcli connection down <profile>
$ nmcli connection edit <profile>
nmcli> set ipv4.method auto
nmcli> set connection.autoconnect yes
nmcli> verify
nmcli> save
nmcli> quit
$ nmcli connection up <profile>
```
