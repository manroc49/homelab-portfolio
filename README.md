# AWS Free Tier Homelab Portfolio

Infrastructure engineering demonstration of enterprise Active Directory, network design, and protocol analysis skills on **$0 infrastructure** using AWS Free Tier.

## What This Repo Contains

**15 complete, integrated projects across three skill levels:**

| Level | Focus | Projects |
|-------|-------|----------|
| **T1: Core Infrastructure** | AD deployment, DNS, OUs, users, groups, basic protocols | N01 - N05 |
| **T2: Security & Policy** | Domain join, delegation, GPOs, password policy, Recycle Bin | N06 - N10 |
| **T3: Advanced Enterprise** | PKI/LDAPS, PSOs, multi-AZ replication, AD FS/SAML, disaster recovery | N11 - N15 |

Each project combines **Active Directory** (self-hosted on AWS EC2), **Packet Tracer** (network design), and **Wireshark** (packet-level proof).

---

## Project Index

### T1: Core Infrastructure

| # | Project | What I Proved | Folder |
|---|---------|---------------|--------|
| 1.1 | DNS SRV Record Registration | DC advertises via `_ldap._tcp.homelab.local` SRV record | [/T1-core-infrastructure/N01-dns-srv-records/](/T1-core-fundamentals/N01-dns-srv-records) |
| 1.2 | Domain Controller Promotion | Windows Server becomes `homelab.local` forest root via LDAP bind | /T1-core-infrastructure/N02-dc-promotion/ |
| 1.3 | Organizational Unit Hierarchy | 4-department OU tree (Admins, IT, HR, Users) for RBAC | /T1-core-infrastructure/N03-ou-hierarchy/ |
| 1.4 | Users, Groups & Nested Membership | Automated 6 users, 4 groups; nested membership via LDAP modify | /T1-core-infrastructure/N04-users-groups/ |
| 1.5 | Flat Network & Protocol Basics | ICMP, TCP handshake, ARP, DHCP DORA on single subnet | /T1-core-infrastructure/N05-protocol-basics/ |

### T2: Security & Policy

| # | Project | What I Proved | Folder |
|---|---------|---------------|--------|
| 2.6 | EC2 Client Domain Join | Kerberos AS-REQ/AS-REP handshake + LDAP bind | /T2-security-policy/N06-domain-join/ |
| 2.7 | OU Delegation (Password Reset) | HR_Staff resets HR OU passwords (least privilege enforcement) | /T2-security-policy/N07-ou-delegation/ |
| 2.8 | Group Policy Drive Mapping | S: drive (\\DC\HRData) mapped via GPO + SMB Tree Connect | /T2-security-policy/N08-gpo-drive-mapping/ |
| 2.9 | Password & Lockout Policy | 8-char complexity, 3-attempt lockout with KRB_ERROR 0x12 | /T2-security-policy/N09-password-lockout/ |
| 2.10 | AD Recycle Bin (Object Recovery) | Deleted objects restored with `isDeleted` TRUE→FALSE | /T2-security-policy/N10-recycle-bin/ |

### T3: Advanced Enterprise

| # | Project | What I Proved | Folder |
|---|---------|---------------|--------|
| 3.11 | PKI & LDAPS (TLS Decryption) | Enterprise CA, LDAPS port 636, TLS 1.3 decryption with SSLKEYLOGFILE | /T3-advanced-enterprise/N11-pki-ldaps/ |
| 3.12 | Fine-Grained Password Policies (PSO) | Admin (14-char) vs HR (8-char) different rules via PSO priority | /T3-advanced-enterprise/N12-fine-grained-password-policies/ |
| 3.13 | Multi-AZ Replication (AD Sites) | Cross-AZ replication via `drsuapi.DRSGetNCChangesRequest/Response` | /T3-advanced-enterprise/N13-multi-az-replication/ |
| 3.14 | AD FS Federation (SAML) | SAMLResponse with NameID + AttributeStatement via HTTP POST | /T3-advanced-enterprise/N14-adfs-saml/ |
| 3.15 | Authoritative Restore (ntdsutil) | OU recovery from DSRM, RTO reduced 2hrs→30min | /T3-advanced-enterprise/N15-authoritative-restore/ |

---

## How Hiring Managers Can Verify My Work

| Path | Time | What You'll See |
|------|------|-----------------|
| **Quickest** (screenshots) | 30 sec | Annotated Packet Tracer diagrams + Wireshark packet screenshots |
| **Medium** (Wireshark) | 2 min | Raw .pcapng files with display filters applied |
| **Deep** (re-run scripts) | 25 min/project | Full reproduction via PowerShell scripts on AWS Free Tier |

---

## Technologies Demonstrated

| Category | Technologies |
|----------|--------------|
| **Cloud** | AWS EC2 t2.micro, VPC, Security Groups, Availability Zones, Free Tier optimization |
| **Active Directory** | DNS SRV records, DC promotion, OUs, Groups, nested membership, Kerberos (AS-REQ/AS-REP), LDAP bind/modify, GPOs, Delegation (dsacls), Recycle Bin, PSOs, Sites & Services, AD FS, ntdsutil |
| **PKI & Security** | Enterprise Root CA + Issuing CA, Domain Controller certificates, LDAPS (port 636), TLS 1.3 decryption, SAML 2.0 |
| **Networking** | Cisco Packet Tracer, flat topology, ICMP, TCP 3-way handshake, ARP, DHCP DORA, RPC, drsuapi |
| **Protocol Analysis** | Wireshark, display filters, TLS decryption (SSLKEYLOGFILE), LDAP packets, Kerberos error codes, SMB Tree Connect, DRS replication |
| **Automation** | PowerShell (Install-ADDSForest, New-ADOrganizationalUnit, New-ADUser, New-ADGroup, Add-ADGroupMember, Enable-ADOptionalFeature, New-ADFineGrainedPasswordPolicy, dsacls) |

---

## Cost Tracking

| Resource | Limit | My Usage | Cost |
|----------|-------|----------|------|
| EC2 t2.micro | 750 hrs/month | ~60 hrs total (all 15 projects) | $0.00 |
| EBS storage (30 GB) | 30 GB | 30 GB (DC1 + DC2 + CA + ADFS) | $0.00 |
| **TOTAL** | | | **$0.00** |

*All projects completed within AWS Free Tier limits. No infrastructure costs incurred.*

---


## Contact

- **GitHub:** [manroc49] (https://github.com/manroc49/homelab-portfolio/blob/main/README.md)
- **LinkedIn:** [https://www.linkedin.com/in/mgr49]
