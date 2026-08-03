# Windows Server 2022 Installation

## Objective

Install Windows Server 2022 on `DC01` and prepare it for Active Directory configuration.

At this stage, DC01 is still a standalone Windows Server.

---

## Installation Media

DC01 successfully booted from the Windows Server 2022 Evaluation ISO.

The following regional settings were selected:

```text
Language: English (United States)
Time and currency format: English (United States)
Keyboard layout: US
```

---

## Windows Server Edition

The selected edition was:

```text
Windows Server 2022 Standard Evaluation
Desktop Experience
```

Standard Edition supports all roles required for this lab, including:

- Active Directory Domain Services
- DNS
- DHCP
- Group Policy
- PowerShell

Desktop Experience was selected because the graphical tools are easier to learn, demonstrate, and document.

---

## Installation Type

The following installation option was selected:

```text
Custom: Install Microsoft Server Operating System only
```

A clean installation was appropriate because the virtual disk contained no previous operating system or data.

---

## Disk Configuration

Windows detected:

```text
Drive 0
60 GB
Unallocated Space
```

Windows automatically created the required GPT partitions because the VM uses UEFI.

These partitions include:

- EFI System Partition
- Microsoft Reserved Partition
- Windows partition
- Recovery partition

The main Windows partition became the `C:` drive.

---

## Installation Process

Windows Setup completed the following tasks:

- Copied operating system files
- Installed Windows features
- Created boot files
- Configured the disk
- Prepared the server for first startup

The VM restarted automatically during installation.

---

## Administrator Account

Windows created the built-in local account:

```text
Administrator
```

This account is used for the initial server configuration before Active Directory and domain accounts exist.

The password was not stored in the repository or screenshots.

---

## First Login

Windows Server started successfully and Server Manager opened after the first login.

This confirmed that:

- Windows Server installed correctly
- Desktop Experience was available
- The Administrator account worked
- The VM could boot from the virtual disk

---

## Installation Summary

| Setting | Configuration |
|---|---|
| Virtual machine | DC01 |
| Operating system | Windows Server 2022 |
| Edition | Standard Evaluation |
| Interface | Desktop Experience |
| Installation type | Custom |
| Disk | 60 GB |
| Firmware | UEFI |
| Secure Boot | Enabled |
| Initial account | Local Administrator |
| Result | Successful |

---

## Next Steps

Before installing Active Directory Domain Services:

1. Rename the Windows computer to `DC01`
2. Install VMware Tools
3. Configure the static IP address `192.168.10.10`
4. Configure DNS
5. Verify date, time, and time zone
6. Install Active Directory Domain Services
7. Promote DC01 to a Domain Controller

---

## Result

Windows Server 2022 was successfully installed on DC01.

The server is ready for post-installation configuration and Active Directory deployment.
