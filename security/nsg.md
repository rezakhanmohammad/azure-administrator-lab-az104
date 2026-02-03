# Network Security Group (NSG)

## Overview
Network Security Groups (NSGs) are used to control inbound and outbound network traffic to Azure resources.  
In this lab, NSGs are implemented to secure the Linux virtual machine by enforcing least-privilege network access.

---

## Resources
- **Resource Group:** `rg-az104-lab`
- **Region:** `West US 2`
- **Virtual Network:** `vnet-az104`
- **Subnet:** `subnet-app`
- **VM:** `vm-az104-linux`
- **NSG:** `nsg-az104-linux`

---

## NSG Design Decision
The NSG is **associated with the subnet**, not the individual NIC.

### Reasoning:
- Subnet-level NSGs provide **consistent security enforcement** for all resources in the subnet
- Easier to manage and scale than NIC-level rules
- Aligns with Azure networking best practices
- Reduces configuration drift

---

## Inbound Security Rules
The following inbound rules are configured:

| Priority | Name        | Port | Source        | Action | Purpose |
|--------|------------|------|---------------|--------|--------|
| 1000   | Allow-SSH  | 22   | Trusted IP / Azure services | Allow  | Secure administrative access |
| 4096   | Deny-All   | Any  | Any           | Deny   | Block all other inbound traffic |

> No public inbound access is allowed by default.

---

## Outbound Security Rules
Outbound traffic uses default Azure rules:
- Allow outbound internet access
- Allow VNet internal communication

This is sufficient for OS updates and outbound connections.

---

## Security Posture
- VM has **no public IP by default**
- SSH access is restricted and intentional
- No unnecessary open ports
- Follows **defense-in-depth** principles
- Designed to support private-only access (Bastion / Jumpbox / VPN)

---

## Validation & Testing
- NSG association verified at subnet level
- Inbound rules reviewed and confirmed
- SSH access tested only when explicitly enabled
- No unintended inbound access observed

---

## Cost & Operational Notes
- NSGs are **free**
- No additional cost incurred
- Centralized security control simplifies operations

---

## Outcome
- Network access is restricted and auditable
- VM is protected against unintended exposure
- Configuration is production-ready and AZ-104 compliant
