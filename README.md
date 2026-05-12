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
| 1 | DNS SRV Records | DC advertises via `_ldap._tcp` SRV record | [/T1-core-infrastructure/01-dns-srv-records/](01-dns-srv-records/) |
| 2 | DC Promotion | Windows Server becomes forest root | [/T1-core-infrastructure/02-dc-promotion/](02-dc-promotion/) |
| 3 | OU Hierarchy | Admins, IT, HR, Users structure for RBAC | [/T1-core-infrastructure/03-ous/](03-ous/) |
| 4 | Users, Groups & Nesting | Automated users, groups, nested membership | [/T1-core-infrastructure/04-users-groups/](04-users-groups/) |
| 5 | Protocol Basics | ICMP, TCP handshake, ARP, DHCP DORA | [/T1-core-infrastructure/05-protocol-basics/](05-protocol-basics/) |

### T2: Security & Policy

| # | Project | What I Proved | Folder |
|---|---------|---------------|--------|
| 6 | EC2 Client Domain Join | Kerberos AS-REQ/AS-REP authentication | [/T2:security-policy/06-domain-join/](06-domain-join/) |
| 7 | OU Delegation | HR resets HR passwords (least privilege) | [/T2:security-policy/07-delegation/](07-delegation/) |
| 8 | GPO Drive Mapping | S: drive mapped via Group Policy | [/T2:security-policy/08-gpo-drive/](08-gpo-drive/) |
| 9 | Password & Lockout Policy | 8-char, complexity, 3-attempt lockout | [/09-password-policy/](09-password-policy/) |
| 10 | AD Recycle Bin | Deleted objects restored in <1 minute | [/T2:security-policy/10-recycle-bin/](10-recycle-bin/) |

### T3 Advanced Enterprise

| # | Project | What I Proved | Folder |
|---|---------|---------------|--------|
| 11 | PKI & LDAPS | Enterprise CA, LDAPS (636), TLS decryption | [/T3:advanced-enterprise/11-pki-ldaps/](11-pki-ldaps/) |
| 12 | Fine-Grained Password Policies (PSO) | Admin (14-char) vs Standard (8-char) rules | [/T3:advanced-enterprise/12-fine-grained-password-policies/](12-fine-grained-password-policies/) |
| 13 | Multi-AZ Replication | Cross-AZ AD replication via RPC/drsuapi | [/T3:advanced-enterprise/13-multi-az-replication/](13-multi-az-replication/) |
| 14 | AD FS Federation (SAML) | SAML 2.0 token issuance for SSO | [/T3:advanced-enterprise/14-adfs-saml/](14-adfs-saml/) |
| 15 | Authoritative Restore (ntdsutil) | OU recovery with ntdsutil in DSRM | [/T3:advanced-enterprise/15-authoritative-restore/](15-authoritative-restore/) |

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
