# Lab Documentation

Technical documentation for the Kane Corp. Windows Help Desk Home Lab.

This section will contain notes about the lab's configuration, networking, Windows administration, troubleshooting, and other technical work as the project develops.

## Network

The lab uses an isolated VMware host-only network so the virtual machines can communicate with each other without being placed directly on my home network.

| Setting | Value |
|---|---|
| VMware Network | VMnet2 |
| Network | 192.168.50.0/24 |
| Subnet Mask | 255.255.255.0 |
| VMware DHCP | Disabled |

### KANE-DC01

| Setting | Value |
|---|---|
| Hostname | KANE-DC01 |
| IPv4 Address | 192.168.50.10 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | None |
| Preferred DNS | 192.168.50.10 |
| DHCP | Disabled |

### Notes

- The server uses a manually configured static IPv4 address.
- The server points to itself for DNS in preparation for the future DNS and Active Directory roles.
- No default gateway is configured because this is an isolated host-only network.
