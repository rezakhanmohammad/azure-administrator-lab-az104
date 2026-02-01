# Compute (Linux VM)

## VM Details
- Resource Group: rg-az104-lab
- Region: West US 2
- VM Name: vm-az104-linux
- OS: Linux (Ubuntu)
- Size: Standard D2als v6 (2 vCPU, 4 GiB)  <!-- اگر فرق داشت اصلاح کن -->
- VNet/Subnet: vnet-az104 / subnet-web
- Private IP: 10.10.1.4  <!-- اگر فرق داشت اصلاح کن -->
- Public IP: None (No public inbound access)

## Security Notes
- Public IP removed to reduce attack surface
- Access is intended via:
  - Azure Bastion (recommended), OR
  - Jumpbox inside VNet, OR
  - VPN/Private connectivity (future)

## CLI Verification Commands

### List VM and power state
```bash
az vm list -d -o table

## Current Status
- Power state: Deallocated (cost optimized)
