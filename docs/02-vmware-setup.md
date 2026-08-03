# VMware Workstation Setup

## Objective

Create and configure the `DC01` virtual machine for the Active Directory enterprise lab.

DC01 will later provide:

- Active Directory Domain Services
- DNS
- DHCP
- Group Policy
- Centralized authentication

---

## Virtualization Platform

VMware Workstation was used to run the lab environment on one physical computer.

Virtualization allows multiple independent systems to share the host computer's:

- CPU
- Memory
- Storage
- Networking

This reduces hardware costs and makes testing, recovery, and expansion easier.

---

## Host-only Network

The lab uses the VMware Host-only network:

```text
VMnet1
192.168.10.0/24
```

Host-only networking was selected to isolate the lab from the home network.

This prevents future DHCP and DNS services from affecting personal devices.

VMware DHCP was disabled so Windows Server can provide DHCP for the lab.

---

## Addressing Plan

| Address or range | Purpose |
|---|---|
| 192.168.10.10 | DC01 |
| 192.168.10.20 | Future File Server |
| 192.168.10.30 | Future Print Server |
| 192.168.10.100–199 | Client workstations |
| 192.168.10.200–254 | Future expansion |

DC01 will use a static IP address so clients and network services can always locate it.

---

## Virtual Machine Configuration

The VM was named:

```text
DC01
```

The name identifies it as the first Domain Controller in the environment.

The following virtual hardware was configured:

| Component | Configuration |
|---|---|
| Guest OS | Windows Server 2022 |
| Firmware | UEFI |
| Secure Boot | Enabled |
| CPU | 4 virtual cores |
| Memory | 4 GB |
| Network | Host-only |
| Storage controller | LSI Logic SAS |
| Disk type | NVMe |
| Disk capacity | 60 GB |
| Provisioning | Thin provisioned |
| Disk file | DC01.vmdk |

The server was right-sized for a small Active Directory lab without assigning unnecessary host resources.

---

## Storage Configuration

A new 60 GB virtual disk was created.

Thin provisioning was used so the virtual disk grows as data is added instead of consuming the full 60 GB immediately.

The disk was stored as one file:

```text
DC01.vmdk
```

---

## Windows Server Installation Media

The Windows Server 2022 Evaluation ISO was attached to the virtual CD/DVD drive.

The drive was configured to:

```text
Use ISO image file
Connect at power on
```

The ISO provides the bootable installation media required to install Windows Server.

---

## Result

The DC01 virtual machine was successfully created and configured.

It was ready to boot from the Windows Server 2022 ISO and begin the operating system installation.
