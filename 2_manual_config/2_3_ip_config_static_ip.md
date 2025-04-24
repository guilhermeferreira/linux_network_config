# iproute

The `ip` command is used to configure network interfaces on modern systems.

## ip address

Can use `ip addr`, or `ip a`.

| Command | Description |
|---------|-------------|
| `ip a` | Show active interfaces |
| `ip a add <ipaddr> dev <iface>` | Assign an address to the interface |

## ip link

Can use `ip l`.

| Command | Description |
|---------|-------------|
| `ip l set <iface> up` | Make an interface active |

## ip route

Can use `ip r`.

| Command | Description |
|---------|-------------|
| `ip r add default via <ipaddr> dev <iface>` | Add a default route |
 