# Azure Hybrid Networking Lab
🔗 by ifeOps

This is a real-world Azure networking project that simulates a secure hybrid infrastructure using:

- ✅ Site-to-Site VPN
- ✅ VNet Peering (Global)
- ✅ Private DNS Zones
- ✅ Bastion Host Access
- ✅ Cross-VNet VM Connectivity

---

## 🧠 Architecture Overview

![Architecture Diagram](architecture-diagram.png)

### Key Setup:
- **Branch (On-Prem Simulation)**: UK West VNet with VPN Gateway
- **HQ**: West US VNet with Gateway Transit Enabled
- **Analytics Unit**: Peered to HQ (remote gateway enabled)
- **VMs**: Deployed in each VNet to test DNS and connectivity
- **DNS Zone**: `mydearsite.com` for internal name resolution
- **Bastion**: Deployed in Branch & HQ for secure RDP/SSH

---

## 🛠️ Configuration Summary

### 🔐 Site-to-Site VPN
- Configured using Virtual Network Gateway + Local Network Gateway
- Shared key stored in `vpn-shared-key.txt`
- Connected Branch VNet (UK) to HQ VNet (US)

### 🌍 Global VNet Peering
- HQ ↔ Analytics Unit
- Enabled gateway transit at HQ
- Enabled “Use remote gateway” at Analytics Unit

### 🌐 Private DNS
- Zone: `mydearsite.com`
- Linked to all VNets (auto-registration only for HQ)
- Custom record sets created after VMs were deployed

---

## 🧪 Testing + Validation
- VMs could **ping each other by DNS name**
- **No public IP** needed to resolve names
- Tested with `ping hqvm.mydearsite.com` from Branch
- Verified peering and VPN connections

---

## 🧰 Tools Used
- Azure Portal
- Azure Bastion
- NSG Inbound Rules
- Diagnostics Logs
- Private DNS

---

## 📸 Screenshots

See the `/screenshots` folder for:
- DNS resolution success
- Ping tests across VNets
- VPN gateway status

---

## 🌍 Author

**ifeOps** — Cloud | DevOps | Networking on Azure  
🟦 [LinkedIn](https://www.linkedin.com/in/adewuyi-ifeoluwa/)  
🐙 [GitHub](https://github.com/A-Ifeoluwa)
