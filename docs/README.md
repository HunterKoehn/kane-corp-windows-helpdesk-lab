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

## Active Directory

`KANE-DC01` has been promoted to the first Domain Controller for the Kane Corp. lab.

- Domain: `kane.local`
- NetBIOS domain name: `KANE`
- Domain Controller: `KANE-DC01`
- DNS: Installed on `KANE-DC01`
- Global Catalog: Enabled
- Domain Controller type: Writable

## DNS

DNS was installed as part of the Active Directory Domain Services deployment.

The `kane.local` DNS zone was created automatically when `KANE-DC01` was promoted to a Domain Controller.

### Verified DNS Zones

- `kane.local`
- `_msdcs.kane.local`

The `kane.local` zone contains Active Directory-related records including:

- `_msdcs`
- `_sites`
- `_tcp`
- `_udp`
- `DomainDnsZones`
- `ForestDnsZones`

### KANE-DC01 DNS Record

`KANE-DC01` has an IPv4 host record pointing to:

`192.168.50.10`

This DNS configuration allows Active Directory clients to locate the Domain Controller and other domain services.

## Active Directory Organizational Structure

The Active Directory environment uses Organizational Units (OUs) to organize servers, workstations, employee accounts, and security groups.

### Organizational Units

```text
kane.local
├── Groups
├── Employee Users
│   ├── Accounting
│   ├── HR
│   ├── IT
│   ├── Sales
│   └── Management
├── Servers
└── Workstations
```

The built-in Users, Computers, and Domain Controllers containers/OUs were left unchanged.

Purpose
- Servers — server computer accounts
- Workstations — Windows workstation computer accounts
- Employee Users — employee user accounts
- Department OUs — organize employees by department
- Groups — security groups used for access control and permissions
