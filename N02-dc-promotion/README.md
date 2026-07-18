# Project 1.2: Domain Controller Promotion

**Tagline:** Documenting the LDAP bindRequest/bindResponse that proves a Windows Server has been promoted to a Domain Controller.

## What This Proves

| Concept | Evidence |
|---------|----------|
| LDAP service is running on port 389 | ldp.exe successfully binds to DC |
| DC accepts LDAP authentication | ldp.exe bind returns "Authenticated as homelab\Administrator" |
| LDAP bindRequest is sent from client | Wireshark capture showing bindRequest packet |
| LDAP bindResponse confirms success | Wireshark capture showing bindResponse with success |

## Topology

| Device | Role | IP Address | OS |
|--------|------|------------|-----|
| DC | Domain Controller + LDAP Server | DHCP-assigned (172.31.x.x) | Windows Server 2025 |
| Client | ldp.exe (on DC itself) | 127.0.0.1 | N/A |

## IP Addressing Plan

| Network | Subnet | Gateway |
|---------|--------|---------|
| homelab.local | AWS VPC (172.31.0.0/16) | AWS Default Gateway |

## Configuration Files

| File | Purpose |
|------|---------|
| N02-dc-promotion-topology.pkt | Packet Tracer topology with LDAP/Kerberos port labels |

## Step-by-Step Configuration

    # Phase 1: Start AWS instance (reuse existing DC)
    # - AWS Console → EC2 → Instances → Start DC-homelab

    # Phase 2: RDP into DC
    # - Use same credentials as Project 1.1

    # Phase 3: Open Packet Tracer, reuse topology from N01
    # - Add labels: LDAP port 389, Kerberos port 88

    # Phase 4: Open Wireshark and start capture on Ethernet

    # Phase 5: Open ldp.exe (built into Windows Server)
    # - Start → type "ldp" → press Enter

    # Phase 6: Connect to DC
    # - Connection → Connect → Server: 127.0.0.1 → Port: 389 → OK

    # Phase 7: Bind to DC
    # - Connection → Bind → Bind with credentials
    # - Username: HOMELAB\Administrator
    # - Password: [AWS password from Project 1.1]
    # - Click OK

    # Phase 8: Stop Wireshark capture
    # - Filter: ldap.bindRequest or ldap.bindResponse

    # Phase 9: Stop AWS instance

## Verification Commands

| Command | Expected Result |
|---------|----------------|
| ldp.exe bind to 127.0.0.1:389 | "Authenticated as homelab\Administrator" |
| Wireshark filter `ldap.bindRequest` | Shows bindRequest packet |
| Wireshark filter `ldap.bindResponse` | Shows bindResponse with success |

## Issues Encountered

| Issue | Resolution |
|-------|------------|
| ldp.exe fails to bind | Verify DNS resolution: `nslookup homelab.local` |
| Wireshark shows no LDAP traffic | Use filter `ldap` instead of specific filter |
| RDP connection lost | Use HOMELAB\Administrator as username |

## What I Would Do Differently

- Use ldp.exe immediately rather than trying to generate bind traffic with PowerShell
- Reuse existing DC instead of rebuilding

## Files in Folder

| File | Description |
|------|-------------|
| README.md | This file |
| blog-post.md | Companion blog post |
| N02-dc-promotion-topology.pkt | Packet Tracer topology |
| N02-ldap-bind-capture.pcapng | Wireshark capture |
| screenshots/ | Annotated evidence images |

## Estimated Time

| Phase | Time |
|-------|------|
| Start AWS instance | 2 min |
| Packet Tracer topology update | 5 min |
| RDP connection | 2 min |
| ldp.exe bind test | 5 min |
| Wireshark capture | 10 min |
| Screenshots & documentation | 10 min |
| **Total** | **34 min** |
