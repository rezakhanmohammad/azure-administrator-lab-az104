# Azure Administrator Lab Project (AZ-104)

##  Project Overview
This repository contains a hands-on Azure Administrator lab project built as part of AZ-104 preparation.

The scenario simulates a **small company** that needs a **secure Linux server** hosted in Microsoft Azure, following best practices for networking, security, monitoring, backup, and automation.

---

##  Architecture Overview
- Resource Group: `rg-az104-lab`
- Region: West US 2
- Virtual Network (VNet) with dedicated subnet
- Linux Virtual Machine
- Network Security Group (NSG)
- Azure Monitor & Alerts
- Azure Backup (Recovery Services Vault)
- Role-Based Access Control (RBAC)
- Automation for VM Start/Stop

---

##  Security
- Least-privilege RBAC
- Restricted inbound traffic using NSG
- SSH key-based access
- No unnecessary public exposure

---

##  Azure Services Used
- Azure Virtual Network
- Azure Virtual Machines (Linux)
- Network Security Groups (NSG)
- Azure Monitor & Log Analytics
- Recovery Services Vault
- Azure Automation
- Azure CLI / PowerShell

---

##  Project Goal
Demonstrate real-world Azure Administrator skills suitable for:
- AZ-104 Exam
- Junior / Mid-level Azure Administrator roles

---

##  Notes
This project was built using a **hands-on, production-style approach** — no theory-only labs.

