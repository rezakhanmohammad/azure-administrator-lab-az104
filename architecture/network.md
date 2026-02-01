# Network Architecture

## Overview
This lab implements a secure and simple network architecture for a small company workload hosted in Microsoft Azure.

The design follows Azure networking best practices, focusing on isolation, least privilege, and scalability.

---

## Virtual Network (VNet)
- **Name:** vnet-az104
- **Resource Group:** rg-az104-lab
- **Region:** West US 2
- **Address Space:** 10.10.0.0/16

The VNet provides isolated networking for all Azure resources used in this project.

---

## Subnet Design
### Web Subnet
- **Name:** subnet-web
- **Address Prefix:** 10.10.1.0/24

This subnet hosts the Linux Virtual Machine used by the company.

Reasons for subnet separation:
- Improved security boundaries
- Easier NSG management
- Scalability for future workloads

---

## Security Considerations
- Network Security Groups (NSGs) are applied at the subnet level
- Only required inbound ports are allowed
- No public IP is assigned unless explicitly required
- Traffic is filtered using least-privilege rules

---

## Result
This network design provides:
- Secure isolation of resources
- Controlled inbound/outbound traffic
- A foundation ready for production-style workloads
