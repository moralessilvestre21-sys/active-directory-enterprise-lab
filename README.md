
# Active Directory Enterprise Lab

An enterprise-style Windows domain environment built in VMware Workstation Pro to gain hands-on experience with **Active Directory, Windows Server, DNS, DHCP, Group Policy, access control, PowerShell, and troubleshooting**.

The lab simulates a small organization's Windows infrastructure using a Windows Server 2022 domain controller and a Windows 11 domain-joined workstation.

---

## Lab Overview

| Component | Configuration |
| --- | --- |
| Domain | `corp.homelab.local` |
| Domain Controller | `DC01` |
| DC IP Address | `192.168.10.10` |
| Client | `CLIENT01` |
| Network | VMware VMnet1 (Host-only) |
| Subnet | `192.168.10.0/24` |
| Server Roles | AD DS, DNS, DHCP |

### Technologies

- Windows Server 2022
- Windows 11 Pro
- Active Directory Domain Services
- DNS & DHCP
- Group Policy
- PowerShell
- NTFS & SMB Permissions
- VMware Workstation Pro
- Git & GitHub

---

## Active Directory Environment

I deployed `DC01` as the domain controller for `corp.homelab.local` and organized the domain using Organizational Units for employees, workstations, and servers.

```text
corp.homelab.local
│
├── Employees
│   ├── IT
│   ├── HR
│   ├── Finance
│   └── Sales
│
├── Workstations
│   └── CLIENT01
│
└── Servers
```

Domain users and security groups were created to simulate departmental access and administration.

`CLIENT01` was joined to the domain and successfully authenticated users through `DC01`.

---

## DNS & DHCP

`DC01` provides both DNS and DHCP services for the lab.

DNS allows domain clients to locate Active Directory resources, while DHCP centrally provides client network configuration.

`CLIENT01` successfully received:

```text
IPv4 Address : 192.168.10.100
DHCP Server  : 192.168.10.10
DNS Server   : 192.168.10.10
```

Connectivity and name resolution were validated using `ipconfig`, `ping`, and `nslookup`.

---

## Group Policy

I configured Group Policy to restrict employee access to **Control Panel and Windows Settings**.

The policy was tested against domain users, and **security filtering** was used to exclude the IT security group so IT personnel could retain access.

Policy processing was verified using:

```cmd
gpresult /r
```

This demonstrated how **OU placement, GPO scope, and security filtering** work together to centrally manage users.

---

## Role-Based File Access

A protected Finance network share was created:

```text
\\DC01\Finance
```

Access was assigned through the `GG_Finance` Active Directory security group instead of directly to individual users.

```text
Finance Employee → GG_Finance → \\DC01\Finance
```

Testing confirmed that a Finance employee could create and modify files while a user outside `GG_Finance` was denied access.

This demonstrated **group-based authorization, NTFS/SMB permissions, and least-privilege access control**.

---

## PowerShell Administration

PowerShell was used to query and administer Active Directory.

Examples included:

```powershell
Get-ADGroupMember -Identity "GG_Finance"

Get-ADUser -Filter * -SearchBase "OU=Finance,OU=Employees,DC=corp,DC=homelab,DC=local"

Get-ADUser -Identity "temployee"

Remove-ADUser -Identity "temployee"
```

I also used `New-ADUser` to create and verify a temporary domain account before removing it, demonstrating basic **AD user lifecycle administration**.

---

## Troubleshooting

One of the most valuable parts of the project was diagnosing a DHCP/network failure.

`CLIENT01` unexpectedly received a `169.254.x.x` **APIPA address**, indicating that it could not reach a DHCP server.

I investigated:

- Client IP configuration
- VMware virtual networking
- DHCP service and authorization
- DHCP event logs
- DC connectivity
- DNS resolution

The issue was traced to the **VMware Host-only network configuration**, which was no longer operating with the lab's intended `192.168.10.0/24` configuration.

After restoring VMnet1 and verifying DHCP authorization, `CLIENT01` successfully obtained `192.168.10.100`.

Connectivity and DNS were then validated with:

```cmd
ping 192.168.10.10
nslookup corp.homelab.local
```

This reinforced the importance of troubleshooting from the underlying **network layer upward** instead of assuming the visible Windows service is the root cause.

---

## Skills Demonstrated

- Active Directory Domain Services
- Windows Server Administration
- Users, Groups & Organizational Units
- Windows Domain Authentication
- DNS & DHCP Administration
- Group Policy & Security Filtering
- NTFS & SMB Permissions
- Role-Based Access Control
- PowerShell Administration
- VMware Networking
- TCP/IP Troubleshooting
- Technical Documentation

---

## Project Status

- [x] Windows Server 2022 deployment
- [x] Active Directory Domain Services
- [x] DNS and DHCP
- [x] OU, user, and security group administration
- [x] Windows 11 domain join
- [x] Group Policy and security filtering
- [x] Finance network share and permissions
- [x] PowerShell AD administration
- [x] Network and DHCP troubleshooting
- [x] Final service validation

---

## Key Takeaway

This project helped me understand Active Directory as an **interconnected Windows environment** rather than a collection of individual server features.

Building and troubleshooting the lab demonstrated how networking, DNS, DHCP, authentication, Group Policy, security groups, and permissions work together to centrally manage users and computers.

Detailed implementation notes, screenshots, diagrams, and troubleshooting documentation are included throughout this repository.
