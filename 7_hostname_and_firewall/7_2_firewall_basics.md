# Firewall

A firewall controls what network traffic is allowed to travel in and out of the system.

## Packet Filtering

There are two network filtering softwares on Linux:
- `iptables` legacy, it uses separate tables and chains (rulesets).
- `nftables` modern, it uses a single ruleset.

A Packet Filtering Framework interacts with netfilter, the kernel component that handles packet filtering and NAT (Network Address Translation).

Rules are organized into tables (filter, nat, mangle, raw) and chains (INPUT, OUTPUT, FORWARD).

It operates at the per-packet level, evaluating each network packet against a set of rules.

## Firewall Manager

A Firewall Manager offers a simple interface for the Packet Filtering Framework.

There are two firewall managment tools:
- `firewalld` manages `iptables` and `nftables` rules on Red Hat systems.
- `ufw` manages `iptables` rules on Ubuntu systems.
