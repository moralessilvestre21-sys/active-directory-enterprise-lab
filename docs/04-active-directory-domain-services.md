# Active Directory Domain Services

Active Directory Domain Services (AD DS) was deployed to create a centralized Windows domain for managing users, computers, authentication, and organizational resources.

## Configuration

- Renamed the Windows Server to `DC01`.
- Assigned DC01 the static IP address `192.168.10.10`.
- Installed the Active Directory Domain Services role.
- Promoted DC01 to a Domain Controller.
- Created a new Active Directory forest.
- Configured the domain as `corp.homelab.local`.
- Installed DNS as part of the domain controller deployment.
- Enabled the Global Catalog.

## Design Decisions

A new forest was created because the lab did not have an existing Active Directory environment.

DC01 uses a static IP address so domain clients have a consistent location for critical services such as Active Directory and DNS.

## Result

DC01 now provides centralized authentication and directory services for the `corp.homelab.local` domain.
