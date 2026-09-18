# DHCP Configuration

DHCP was configured on Windows Server to centrally manage IP addressing for devices in the lab network.

## Configuration

- Disabled VMware DHCP on VMnet1.
- Installed and configured the Windows Server DHCP role.
- Authorized the DHCP server in Active Directory.
- Configured DHCP for the `192.168.10.0/24` network.
- Reserved lower addresses for infrastructure and server systems.
- Designed the workstation range around `192.168.10.100-199`.
- Configured domain clients to use DC01 for DNS.

## Design Decision

VMware DHCP was disabled so Windows Server would be responsible for address management. This prevents competing DHCP services and more closely represents a centrally managed enterprise environment.

## Validation

CLIENT01 successfully received the expected network configuration after DHCP connectivity was restored.

The APIPA/DHCP issue encountered during this deployment is documented separately in `12-troubleshooting.md`.
