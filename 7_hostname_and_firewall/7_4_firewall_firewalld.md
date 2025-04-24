# Firewall configuration with Firewalld

| Command | Description |
|---------|-------------|
| `firewall-cmd --list-all` | Show all the zones (collection of rules that apply to all networks) |
| `firewall-cmd --add-service=ssh` | Allow access for SSH (TCP port 22) using service name until the next reboot |
| `firewall-cmd --add-port=22/tcp` | Allow access for SSH (TCP port 22) using port number until the next reboot |
| `firewall-cmd --add-service=ssh --permanent` | Allow access for SSH (TCP port 22) using service name |
| `firewall-cmd --add-port=22/tcp --permanent` | Allow access for SSH (TCP port 22) using port number |
| `firewall-cmd --remove-service=ssh` | Block access to SSH (TCP port 22) using service name |
| `firewall-cmd --add-service=22/tcp` | Block access to SSH (TCP port 22) using port number |
