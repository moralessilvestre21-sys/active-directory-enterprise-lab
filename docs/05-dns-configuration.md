# DNS Configuration

DNS was configured as part of the Active Directory deployment because Active Directory relies heavily on DNS to locate domain controllers and domain services.

## Configuration

- Installed DNS alongside Active Directory Domain Services.
- Configured DC01 as the DNS server for the domain.
- Verified the `corp.homelab.local` DNS namespace.
- Configured CLIENT01 to use `192.168.10.10` as its DNS server.
- Tested domain name resolution from CLIENT01.

## Validation

DNS resolution was verified using:

`nslookup corp.homelab.local`

CLIENT01 successfully resolved the domain to DC01 at `192.168.10.10`.

## Result

Domain clients can locate DC01 through DNS, allowing Active Directory authentication and domain services to function correctly.
