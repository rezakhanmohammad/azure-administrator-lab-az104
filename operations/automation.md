# Operations – Automation (Scheduled Start/Stop)

## Goal
Reduce cost by automatically starting and deallocating the lab VM on a schedule, while keeping the environment production-like and repeatable.

---

## Resources
- **Resource Group:** `rg-az104-lab`
- **Region:** `West US 2`
- **VM:** `vm-az104-linux`
- **Automation Account:** `aa-autodeallocate-az104` (existing)

---

## Automation Design (High Level)
This lab uses **Azure Automation** to run scheduled jobs that:
- **Start** the VM during working hours (when needed)
- **Deallocate** the VM outside working hours (cost optimization)

> Deallocate is used instead of Stop, because **deallocate releases compute billing**.

---

## Runbooks
### 1) Start VM Runbook
- Action: `az vm start`
- Target: `rg-az104-lab / vm-az104-linux`
- Outcome: VM becomes `VM running`

### 2) Deallocate VM Runbook
- Action: `az vm deallocate`
- Target: `rg-az104-lab / vm-az104-linux`
- Outcome: VM becomes `VM deallocated`

---

## Scheduling (Example)
> Adjust hours based on your timezone and needs.

- **Weekdays Start:** 8:00 AM (Mon–Fri)
- **Weekdays Deallocate:** 6:00 PM (Mon–Fri)

This ensures the VM is available during typical working hours and cost-optimized outside them.

---

## Security Notes
- Automation Account uses least-privilege access:
  - Assign only the required role at **resource group scope** (recommended: `Virtual Machine Contributor`)
- No public inbound access is required for automation.
- Schedules and runbook execution are auditable through Job history.

---

## CLI Verification
### Check VM state
```bash
az vm list -d -o table

