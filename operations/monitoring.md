# Azure Monitoring & Alerts

## Overview
Azure Monitor is used to observe the health, performance, and availability of the Linux virtual machine.  
Monitoring includes metrics, alerts, and diagnostic logging to ensure operational visibility and proactive issue detection.

---

## Monitoring Architecture
- **Service:** Azure Monitor
- **Target Resource:** Linux VM (vm-az104-linux)
- **Resource Group:** rg-az104-lab
- **Region:** West US 2
- **Log Platform:** Azure Monitor Metrics (Log Analytics optional)

---

## Metrics Monitoring
The following VM metrics are monitored using Azure Monitor:

- **Percentage CPU**
- **Network In Total**
- **Network Out Total**
- **Disk Read Bytes**
- **Disk Write Bytes**

Metrics provide real-time and historical visibility into VM performance and usage patterns.

---

## Alert Configuration
An Azure Monitor alert rule was created and validated with the following characteristics:

- **Signal Type:** Metric
- **Metric:** Percentage CPU
- **Condition:** CPU usage greater than 80%
- **Evaluation Frequency:** Default
- **Severity:** Informational / Warning (lab configuration)
- **Scope:** Single VM

The alert was tested and later removed to avoid unnecessary cost during idle periods.

---

## Alert Lifecycle Management
- Alert rule creation was validated
- Alert visibility confirmed in Azure Monitor
- Alert rule deletion verified to ensure no active alert rules remain
- This demonstrates full alert lifecycle management (create → validate → remove)

---

## Diagnostic Logs (Optional / Awareness)
Diagnostic settings can be enabled to send logs and metrics to:
- Log Analytics Workspace
- Storage Account
- Event Hub

This lab focuses primarily on metric-based monitoring, which aligns with common AZ-104 exam scenarios.

---

## Cost & Operational Considerations
- Metric-based alerts have minimal cost
- Alerts were removed when not needed to avoid unnecessary charges
- Monitoring is configured without requiring public network access
- Solution follows least-cost and least-noise monitoring principles

---

## CLI Verification (Optional)
```bash
az monitor metrics list \
  --resource vm-az104-linux \
  --resource-group rg-az104-lab \
  --metric "Percentage CPU"

