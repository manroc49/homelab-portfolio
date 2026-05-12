# AWS Free Tier Homelab Portfolio


Infrastructure engineering demonstration of enterprise Active Directory, network design, and protocol analysis skills on **$0 infrastructure** using AWS Free Tier.

## What This Repo Contains

**15 complete, integrated projects across three skill levels:**

| Level | Focus | Projects |
|-------|-------|----------|
| **T1: Core Infrastructure** | AD deployment, DNS, OUs, users, groups, basic protocols | 1-5 |
| **T2: Security & Policy** | Domain join, delegation, GPOs, password policy, Recycle Bin | 6-10 |
| **T3: Advanced Enterprise** | PKI/LDAPS, PSOs, multi-AZ replication, AD FS/SAML, disaster recovery | 11-15 |

Each project combines **Active Directory** (self-hosted on AWS EC2), **Packet Tracer** (network design), and **Wireshark** (packet-level proof).

---

## Project Index

### T1: Core Infrastructure

| # | Project | What I Proved | Folder |
|---|---------|---------------|--------|
| N01 | DNS SRV Records | DC advertises via `_ldap._tcp` SRV record | [/T1-core-infrastructure/N01-dns-srv-records/](N01-dns-srv-records/) |
| N02 | DC Promotion | Windows Server becomes forest root | [/T1-core-infrastructure/N02-dc-promotion/](N02-dc-promotion/) |
| N03 | OU Hierarchy | Admins, IT, HR, Users structure for RBAC | [/T1-core-infrastructure/N03-ous/](N03-ous/) |
| N04 | Users, Groups & Nesting | Automated users, groups, nested membership | [/T1-core-infrastructure/N04-users-groups/](N04-users-groups/) |
| N05 | Protocol Basics | ICMP, TCP handshake, ARP, DHCP DORA | [/T1-core-infrastructure/N05-protocol-basics/](N05-protocol-basics/) |

### T2: Security & Policy

| # | Project | What I Proved | Folder |
|---|---------|---------------|--------|
| N06 | EC2 Client Domain Join | Kerberos AS-REQ/AS-REP authentication | [/T2-security-policy/N06-domain-join/](06-domain-join/) |
| N07 | OU Delegation | HR resets HR passwords (least privilege) | [/T2-security-policy/N07-delegation/](N07-delegation/) |
| N08 | GPO Drive Mapping | S: drive mapped via Group Policy | [/T2-security-policy/N08-gpo-drive/](N08-gpo-drive/) |
| N09 | Password & Lockout Policy | 8-char, complexity, 3-attempt lockout | [/T2-N09-password-policy/](N09-password-policy/) |
| N10 | AD Recycle Bin | Deleted objects restored in <1 minute | [/T2-security-policy/N10-recycle-bin/](N10-recycle-bin/) |

### T3: Advanced Enterprise

| # | Project | What I Proved | Folder |
|---|---------|---------------|--------|
| N11 | PKI & LDAPS | Enterprise CA, LDAPS (636), TLS decryption | [/T3:advanced-enterprise/N11-pki-ldaps/](N11-pki-ldaps/) |
| N12 | Fine-Grained Password Policies (PSO) | Admin (14-char) vs Standard (8-char) rules | [/T3:advanced-enterprise/N12-fine-grained-password-policies/](N12-fine-grained-password-policies/) |
| N13 | Multi-AZ Replication | Cross-AZ AD replication via RPC/drsuapi | [/T3:advanced-enterprise/N13-multi-az-replication/](N13-multi-az-replication/) |
| N14 | AD FS Federation (SAML) | SAML 2.0 token issuance for SSO | [/T3:advanced-enterprise/N14-adfs-saml/](N14-adfs-saml/) |
| N15 | Authoritative Restore (ntdsutil) | OU recovery with ntdsutil in DSRM | [/T3:advanced-enterprise/N15-authoritative-restore/](N15-authoritative-restore/) |

---

## How Hiring Managers Can Verify My Work

| Path | Time | What You'll See |
|------|------|-----------------|
| **Quickest** (screenshots) | 30 sec | Annotated images |
| **Medium** (Wireshark) | 2 min | Raw packet captures |
| **Deep** (re-run scripts) | 25 min/project | Full reproduction |

## Technologies Demonstrated

| Category | Technologies |
|----------|--------------|
| **Cloud** | AWS EC2, VPC, Security Groups, Free Tier optimization |
| **Active Directory** | DNS SRV, OUs, Groups, Kerberos, LDAP, LDAPS, GPOs, Delegation, Recycle Bin, PSOs, Sites & Services, AD FS, ntdsutil |
| **PKI & Security** | Enterprise CA, Domain Controller certificates, TLS decryption, SAML 2.0 |
| **Networking** | Cisco Packet Tracer, RPC, drsuapi |
| **Protocol Analysis** | Wireshark, filters, TLS decryption, DRS replication |
| **Automation** | PowerShell (all 15 projects scripted) |

## Cost Tracking

| Resource | Limit | My Usage | Cost |
|----------|-------|----------|------|
| EC2 t2.micro | 750 hrs/month | ~60 hrs total (all 15 projects) | $0.00 |
| EBS storage | 30 GB | 30 GB | $0.00 |
| **TOTAL** | | | **$0.00** |

## Contact

- **GitHub:** [yourusername] (this repo)
- **LinkedIn:** [linkedin.com/in/yourname]

---

*"I don't just claim skills. I capture the packets that prove them."*
