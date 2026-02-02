# Azure Backup (Recovery Services Vault)

## Overview
Azure Backup is configured to protect the Linux virtual machine against accidental deletion, data corruption, and service outages.  
Backups are managed using a Recovery Services Vault located in the same region as the workload to ensure compliance and performance.

---

## Backup Architecture
- **Recovery Services Vault:** rsv-az104-lab
- **Resource Group:** rg-az104-lab
- **Region:** West US 2
- **Protected Resource:** Linux Virtual Machine (vm-az104-linux)

---

## Backup Configuration
- **Backup Type:** Azure VM Backup
- **Backup Policy:** Daily (default policy)
- **Retention:** Daily recovery points (default retention)
- **Backup Method:** Snapshot-based, application-consistent when supported
- **Backup Schedule:** Automated daily backups

---

## On-Demand Backup
An initial on-demand backup was triggered manually after enabling protection to:
- Validate backup configuration
- Create the first recovery point
- Ensure the VM is successfully protected

---

## Restore Validation
Backup restore functionality was validated using Azure Backup restore options:

- **Restore Option Tested:** Restore managed disks (non-destructive test)
- **Purpose:**
  - Verify backup integrity
  - Validate restore workflow without impacting production VM

No production workload was modified during restore validation.

---

## Security & Cost Considerations
- Backup data is encrypted and managed by Azure
- No public network access is required for backup or restore operations
- Restore testing avoided creating long-running VMs to minimize cost
- Backup aligns with least-privilege and operational best practices

---

## CLI Verification (Optional)
```bash
az backup vault list -o table
1
