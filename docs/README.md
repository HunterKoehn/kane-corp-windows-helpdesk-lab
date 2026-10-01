# Lab Documentation

Technical documentation for the Kane Corp. Windows Help Desk Home Lab.

This section will contain notes about the lab's configuration, networking, Windows administration, troubleshooting, and other technical work as the project develops.

## Network

The lab uses an isolated VMware host-only network so the virtual machines can communicate with each other without being placed directly on my home network.

- Network: `192.168.50.0/24`
- Subnet Mask: `255.255.255.0`
- VMware Network: `VMnet2`
- DHCP: Disabled
- Server: `KANE-DC01`
- Server IP: `192.168.50.10`
