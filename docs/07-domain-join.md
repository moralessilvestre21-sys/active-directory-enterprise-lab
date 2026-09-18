# Domain Join

A Windows 11 Pro workstation was deployed and joined to the Active Directory domain to test centralized authentication and management.

## CLIENT01 Configuration

- Installed Windows 11 Pro.
- Renamed the workstation to `CLIENT01`.
- Connected CLIENT01 to the VMware Host-only network.
- Configured DC01 (`192.168.10.10`) as the DNS server.
- Verified connectivity between CLIENT01 and DC01.
- Joined CLIENT01 to `corp.homelab.local`.
- Restarted the workstation and signed in using a domain account.

## Validation

Domain authentication was verified with:

`whoami`

Result:

`corp\ajohnson`

The authenticating domain controller was verified with:

`echo %logonserver%`

Result:

`\\DC01`

## Result

CLIENT01 became a domain-managed workstation capable of authenticating Active Directory users and receiving centralized policies.
