# Compute (Linux VM)

## VM Details
- Resource Group: rg-az104-lab
- Region: West US 2
- VM Name: vm-az104-linux
- OS: Linux (Ubuntu)
- Size: Standard D2als v6 (2 vCPU, 4 GiB)  <!-- اگر فرق داشت اصلاح کن -->
- VNet/Subnet: vnet-az104 / subnet-web
- Private IP: 10.10.1.4  <!-- اگر فرق داشت اصلاح کن -->
- Public IP: Disabled (cost optimization and security)
- Public IP can be temporarily enabled for maintenance if required

## Security Notes
- No public inbound access by default
- Public IP disabled to minimize cost and attack surface
- Access is intended via:
  - Azure Bastion (recommended)
  - Jumpbox inside VNet
  - VPN / Private connectivity (future)
- VM operates as a private/internal server
## CLI Verification Commands

### List VM and power state
```bash
az vm list -d -o table

## Current Status
- Power state: Deallocated (cost optimized)
