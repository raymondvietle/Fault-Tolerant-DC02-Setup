# Installing a Second Domain Controller in Active Directory Domain Services for Fault Tolerance

## Overview
This project demonstrates how to configure a **second Domain Controller (DC02)** for redundancy and fault tolerance in a Windows Server 2022 AD DS environment. This includes domain joining, role installation, and verifying replication between the primary domain controller (DC01) and the secondary (DC02).

---

## Objectives
- Install Windows Server 2022 as DC02
- Join it to the existing `int.itray.com` domain
- Promote DC02 to a domain controller
- Verify DNS and AD DS replication
- Test fault tolerance

---

## Domain Configuration
- **Primary Domain Controller:** DC01 (`192.168.0.1`)
- **Secondary Domain Controller:** DC02 (assigned static IP, DNS points to DC01)
- **Domain:** `int.itray.com`

---

## Key Steps

### 1. Initial Configuration of DC02
- Rename machine to `DC02`
- Set static IP and preferred DNS (pointing to `192.168.0.1`)
- Join domain as `ITRay\Administrator`
- Restart and login using domain credentials

### 2. Promote DC02 to Domain Controller
- Install AD DS role
- Run post-install wizard
- Use same domain `int.itray.com`
- Restart DC02

### 3. Verify DNS & AD Replication
- DC02 recognized as an authoritative DNS server
- Reverse Lookup Zones replicated from DC01
- AD DS successfully shows replicated Organizational Units and users

---

## Replication Test
- Created new OU “TEST” on DC01
- Verified it appears on DC02
- Created a new user inside TEST OU on DC02
- Confirmed the user appears on DC01

---

## Tools Used
- Windows Server 2022
- Active Directory Domain Services
- DNS Manager
- Windows Admin Center

---

## Notes
- Ensures high availability of Active Directory
- Adds redundancy for DNS services
- Easy failover support for client authentication

---

## Author
Raymond Le  
📅 May 2025
