# Operations – Automation (Scheduled Start/Stop)

## Goal
Reduce cost by automatically starting and deallocating the lab VM on a schedule, while keeping the environment production-like and repeatable.

---

## Resources
- **Resource Group:** `rg-az104-lab`
- **Region:** `West US 2`
- **VM:** `vm-az104-linux`
- **Automation Account:** `aa-autodeallocate-az104`

---

## Automation Design (High Level)
This lab uses **Azure Automation** to run scheduled jobs that:

- Start the VM during working hours
- Deallocate the VM outside working hours to reduce cost

> Deallocate is used instead of Stop because **deallocated VMs do not incur compute charges**.

---

## Runbooks

### 1) Start VM Runbook
- Action: `az vm start`
- Target: `rg-az104-lab / vm-az104-linux`
- Result: VM state changes to `VM running`

### 2) Deallocate VM Runbook
- Action: `az vm deallocate`
- Target: `rg-az104-lab / vm-az104-linux`
- Result: VM state changes to `VM deallocated`

---

## Scheduling (Example)
Schedules can be adjusted based on timezone and usage needs.

- **Weekdays Start:** 08:00 (Mon–Fri)
- **Weekdays Deallocate:** 18:00 (Mon–Fri)

This ensures the VM is available during work hours and cost-optimized when not in use.

---

## Security Notes
- Automation Account uses **least-privilege access**
- Role assigned at **resource group scope**
- Recommended role: `Virtual Machine Contributor`
- No public inbound access is required
- All executions are auditable via Automation job history

---

## CLI Verification
Check VM power state:

```bash
az vm list -d -o table
