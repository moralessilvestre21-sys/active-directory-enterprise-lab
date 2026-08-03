# Active Directory Enterprise Lab Planning

## Objective

The objective of this project is to build a complete on-premises Windows enterprise environment using VMware Workstation and Windows Server 2022.

The lab will simulate how an organization centrally manages:

- Users
- Computers
- Authentication
- Authorization
- DNS
- DHCP
- Organizational Units
- Security groups
- Group Policy
- Shared resources
- Administrative tasks

The first server, `DC01`, will eventually provide Active Directory Domain Services, DNS, and DHCP for the isolated lab network.

---

## Why Active Directory Is Used

Without Active Directory, every Windows computer would need to be managed separately.

Administrators would have to create user accounts, apply settings, manage passwords, and configure permissions on every individual computer.

Active Directory provides centralized management.

Instead of maintaining each workstation independently, administrators can manage users, computers, groups, policies, and access permissions from a Domain Controller.

Active Directory will allow this lab to demonstrate:

- Centralized user authentication
- Centralized computer management
- Role-based access through security groups
- Group Policy enforcement
- Domain-joined client computers
- Centralized DNS
- Centralized DHCP
- Administrative automation

---

## Active Directory Compared to Microsoft Entra ID

Active Directory Domain Services is primarily designed for traditional on-premises Windows environments.

Microsoft Entra ID is a cloud-based identity platform used by Microsoft 365, Azure, and other cloud applications.

### Active Directory Domain Services

Commonly manages:

- Windows domain accounts
- Domain-joined computers
- Group Policy
- Kerberos authentication
- LDAP directory services
- Traditional on-premises resources

### Microsoft Entra ID

Commonly manages:

- Cloud identities
- Microsoft 365 access
- Azure resources
- Cloud applications
- Modern authentication
- Conditional Access

Many organizations use both technologies in a hybrid identity environment.

---

## Planned Infrastructure

The lab will begin with the following virtual machines.

| System | Purpose | Memory | Virtual CPU | Storage |
|---|---|---:|---:|---:|
| DC01 | Domain Controller, DNS, and DHCP | 4 GB | 4 cores | 60 GB |
| CLIENT01 | Windows client joined to the domain | 4 GB | 2 cores | 64 GB |

Additional servers may be added later.

| Planned Name | Purpose |
|---|---|
| FS01 | File Server |
| PRT01 | Print Server |
| SQL01 | Database Server |
| DC02 | Additional Domain Controller |

---

## Server Naming Convention

The naming convention identifies the function of each system.

| Name | Meaning |
|---|---|
| DC01 | First Domain Controller |
| DC02 | Second Domain Controller |
| FS01 | First File Server |
| PRT01 | First Print Server |
| SQL01 | First SQL Server |
| CLIENT01 | First client workstation |

A descriptive naming convention makes an environment easier to manage than generic names such as `Windows Server 2022`.

The number allows additional servers with the same role to be added later without changing the naming standard.

For organizations with multiple locations, a location prefix could also be used.

Examples:

```text
LADC01
PHXDC01
LVDC01
