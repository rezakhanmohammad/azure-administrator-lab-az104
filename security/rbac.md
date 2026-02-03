# Role-Based Access Control (RBAC)

## Overview
Azure Role-Based Access Control (RBAC) is used to manage access to Azure resources by assigning permissions to users or groups at specific scopes.

In this lab, RBAC is implemented to ensure **least-privilege access** while maintaining operational flexibility for administration and automation.

---

## Resources
- **Subscription:** Azure subscription 1
- **Resource Group:** `rg-az104-lab`
- **Region:** `West US 2`
- **Primary Resource:** `vm-az104-linux`

---

## Identity Structure
The following identities are used:

- **User:** `az104-user1`
- **Group:** `az104-admins`
- **Automation Identity:** Azure Automation Account (`aa-autodeallocate-az104`)

---

## RBAC Design Decisions

### Group-Based Access (Preferred)
RBAC assignments are primarily applied to **groups**, not individual users.

**Benefits:**
- Easier access management
- Scales better as users are added/removed
- Reduces configuration drift
- Aligns with Azure best practices

---

## Role Assignments

### 1) Contributor (Human Access)
- **Assigned To:** `az104-admins` (Group)
- **Scope:** Resource Group (`rg-az104-lab`)
- **Purpose:**
  - Manage VM lifecycle
  - Configure networking, monitoring, and storage
  - Perform operational tasks without subscription-wide access

---

### 2) Virtual Machine Contributor (Automation)
- **Assigned To:** Automation Account
- **Scope:** Resource Group (`rg-az104-lab`)
- **Purpose:**
  - Start and deallocate VM
  - Execute scheduled automation runbooks
  - No permission to modify networking or security settings

---

### 3) Reader (Optional / Observational Access)
- **Assigned To:** Read-only users (if required)
- **Scope:** Resource Group
- **Purpose:**
  - View resources and configurations
  - No modification rights

---

## Scope Selection Rationale
RBAC is assigned at the **Resource Group level**, not at subscription level.

**Reasons:**
- Limits blast radius
- Prevents accidental changes to unrelated resources
- Matches real-world enterprise access models

---

## Validation & Testing
RBAC configuration was validated by:
- Logging in as assigned user
- Confirming visibility of VM and related resources
- Verifying permitted actions (start/stop VM)
- Confirming restricted actions outside assigned scope

---

## Security Principles Applied
- Least privilege
- Separation of duties
- Group-based access control
- Explicit scope limitation

---

## Outcome
- Access is controlled, auditable, and secure
- Automation operates with minimal required permissions
- RBAC configuration is production-ready and AZ-104 compliant

