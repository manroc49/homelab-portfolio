# Project 1.1: DNS SRV Record Registration

**Tagline:** Proving automatic Domain Controller discovery works by verifying the `_ldap._tcp` SRV record exists and resolves correctly.

## What This Proves

| Concept | Evidence |
|---------|----------|
| DC advertises LDAP service via DNS SRV | DNS Manager showing `_ldap` SRV record in Forward Lookup Zones |
| Clients can auto-discover DC without hardcoding | nslookup returns SRV record with port 389 and hostname |
| DNS role installs correctly with AD DS | SRV record properties show Priority 0, Weight 100, Port 389 |

## Topology

| Device | Role | IP Address | OS |
|--------|------|------------|-----|
| DC | Domain Controller + DNS Server | DHCP-assigned (172.31.x.x) | Windows Server 2025 |
| Client | Not used in this project | N/A | N/A |

## IP Addressing Plan

| Network | Subnet | Gateway |
|---------|--------|---------|
| homelab.local | AWS VPC (172.31.0.0/16) | AWS Default Gateway |

## Configuration Files

| File | Purpose |
|------|---------|
| N01-dns-srv-topology.pkt | Packet Tracer topology design |

## Step-by-Step Configuration

    # Phase 1: Launch AWS EC2 instance with Windows Server 2025
    # - DO NOT configure static IP - leave DHCP enabled
    # - Security group rules: RDP, DNS (UDP), LDAP, Kerberos (TCP 88)

    # Phase 2: Install AD DS and DNS roles (GUI method)
    # - Server Manager → Add Roles and Features
    # - Select: Active Directory Domain Services, DNS Server
    # - If "No static IP" warning appears, click Continue

    # Phase 3: Promote to Domain Controller (GUI method)
    # - Server Manager → yellow triangle → Promote to domain controller
    # - Add a new forest: homelab.local
    # - DSRM password: P@ssw0rd123!
    # - Server restarts automatically

    # Phase 4: Reconnect as HOMELAB\Administrator
    # - Password: original AWS Administrator password (not DSRM password)

    # Phase 5: Verify SRV records exist (GUI method)
    # - DNS Manager → Forward Lookup Zones → homelab.local → _msdcs → _tcp
    # - Verify _ldap SRV record exists

    # Phase 6: Verify SRV record properties
    # - RIGHT-CLICK _ldap → Properties
    # - Confirm: Port 389, Priority 0, Weight 100

    # Phase 7: Verify DNS resolution (PowerShell)
    nslookup -type=SRV _ldap._tcp.homelab.local. 127.0.0.1

## Verification Commands

| Command | Expected Result |
|---------|----------------|
| `nslookup -type=SRV _ldap._tcp.homelab.local. 127.0.0.1` | Returns SRV record with port 389 and hostname |
| DNS Manager → _ldap Properties | Port: 389, Priority: 0, Weight: 100 |

## Issues Encountered

| Issue | Resolution |
|-------|------------|
| RDP connection lost after promoting to DC | Reconnect as `HOMELAB\Administrator` (not just `Administrator`). Wait 2-3 minutes for AD DS to fully initialize. |
| "No static IP addresses were found" validation warning | Click **Continue** and proceed with installation. AWS manages IP addressing via DHCP. |
| `nslookup` returns "Non-existent domain" | Use trailing dot: `_ldap._tcp.homelab.local.` to prevent Windows from appending AWS domain suffixes (`ec2.internal`). |
| `ping dc.homelab.local` fails while nslookup works | Expected behavior. `nslookup` bypasses Windows DNS Client; `ping` uses it. Does not indicate DNS server failure. |
| DNS queries show `ec2.internal` appended in Wireshark | Normal AWS behavior. Trailing dot in nslookup prevents it. SRV record still resolves correctly. |
| Wireshark shows no DNS traffic when filtering `dns.qry.type == 33` | Windows DNS Client handles queries internally. Relied on DNS Manager and nslookup for verification instead. |

## What I Would Do Differently

- Skip the static IP configuration entirely from the beginning. AWS DHCP works fine for AD DS.
- Use the trailing dot in nslookup queries from the start to avoid the `ec2.internal` suffix confusion.
- Focus on DNS Manager and nslookup as primary evidence rather than spending excessive time troubleshooting Wireshark capture issues.

## Screenshots

- [packet-tracer-topology.png](screenshots/01-packet-tracer-topology.png)
- [aws-rdp-connected.png](screenshots/02-aws-rdp-connected.png)
- [ad-dns-installed.png](screenshots/03-ad-dns-installed.png)
- [services-running.png](screenshots/04-services-running.png)
- [dns-srv-verify.png](screenshots/05-dns-srv-verify.png)
- [nslookup-verify.png](screenshots/06-nslookup-verify.png)

## Estimated Time

| Phase | Time |
|-------|------|
| AWS EC2 deployment | 10 min |
| Packet Tracer topology | 5 min |
| Install AD DS + DNS | 10 min |
| Promote to DC | 10 min |
| Verify SRV records | 5 min |
| Screenshots & documentation | 10 min |
| **Total** | **50 min** |
