# Firewall configuration with UFW

We can use both the service name as well the `port/protocol` such as in the `/etc/services`.

| Command | Description |
|---------|-------------|
| `ufw allow ssh` | Allow access for SSH (TCP port 22) using service name |
| `ufw allow 22/tcp` | Allow access for SSH (TCP port 22) using port number |
| `ufw delete allow ssh` | Block access to SSH (TCP port 22) using service name |
| `ufw delete allow 22/tcp` | Block access to SSH (TCP port 22) using port number |



