# Project 1.1: DNS SRV Record Registration

## What This Proves

| Concept | Evidence |
|---------|----------|
| DC advertises LDAP service via DNS SRV | Wireshark capture showing DNS response with port 389 |
| Clients can auto-discover DC without hardcoding | nslookup returns dc.homelab.local |
| DNS role installs correctly with AD DS | Get-DnsServerResourceRecord returns SRV records |

## Topology

| Device | Role | IP Address | OS |
|--------|------|------------|-----|
| DC | Domain Controller + DNS Server | 10.0.1.10 (static) | Windows Server 2019 |
| Client | Not used in this project | N/A | N/A |

## IP Addressing Plan

| Network | Subnet | Gateway |
|---------|--------|---------|
| homelab.local | 10.0.1.0/24 | 10.0.1.1 |

## Configuration Files

| File | Purpose |
|------|---------|
| deploy-dc.ps1 | Automates AD DS + DNS installation and promotion |
| wireshark-filters.txt | Display filter: `dns.qry.type == 33` |

## Step-by-Step Configuration

```powershell
# Phase 1: Set static IP (inside EC2 RDP session)
New-NetIPAddress -InterfaceAlias "Ethernet" -IPAddress 10.0.1.10 -PrefixLength 24 -DefaultGateway 10.0.1.1
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses 127.0.0.1

# Phase 2: Install AD DS and DNS roles
Install-WindowsFeature -Name AD-Domain-Services,DNS -IncludeManagementTools

# Phase 3: Promote to Domain Controller
Install-ADDSForest -DomainName "homelab.local" -InstallDNS -Force

# Phase 4: Verify SRV records
Get-DnsServerResourceRecord -ZoneName "homelab.local" -RRType SRV | Where-Object {$_.RecordName -like "*_ldap*"}

# Phase 5: Generate DNS query for Wireshark
nslookup -type=SRV _ldap._tcp.homelab.local
