# Troubleshooting

During the lab, CLIENT01 unexpectedly lost its DHCP configuration and received an APIPA address:

```text
169.254.157.227
```

An APIPA address indicated that the client was unable to obtain an IPv4 address from the DHCP server.

## Investigation

I investigated the issue by checking:

- CLIENT01 network configuration
- DC01 connectivity
- DHCP service status
- DHCP event logs
- DHCP authorization in Active Directory
- VMware VMnet1 configuration

DHCP authorization was verified with:

```powershell
Get-DhcpServerInDC
```

DC01 was correctly listed as an authorized DHCP server, which helped narrow the problem to the virtual network.

## Root Cause & Resolution

The issue was traced to the **VMware VMnet1 Host-only network configuration**, which no longer matched the lab's intended `192.168.10.0/24` network.

VMnet1 was restored to the correct configuration with VMware DHCP disabled so Windows Server remained responsible for assigning client addresses.

After the correction, CLIENT01 successfully received:

```text
IPv4 Address: 192.168.10.100
DNS Server:   192.168.10.10
```

Connectivity and DNS resolution were verified using:

```cmd
ping 192.168.10.10
nslookup corp.homelab.local
```

## Key Takeaway

This issue reinforced the importance of troubleshooting **from the network layer upward** and verifying each component instead of assuming the first error message identifies the root cause.
