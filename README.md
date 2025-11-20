# 🪟 Windows Server 2019 — ADDS + RAS/NAT + DHCP

This project demonstrates how to deploy a full **Active Directory Domain Services (ADDS)** environment on Windows Server 2019, integrated with **Remote Access Services (RAS/NAT)** and **Dynamic Host Configuration Protocol (DHCP)**. Designed for homelab enthusiasts and cybersecurity professionals, it replicates enterprise-grade identity and network services in a compact, virtualized home network setup.

---

## 📐 Architecture Overview

- **Windows Server 2019** configured as a Domain Controller
- **ADDS** for centralized identity and authentication
- **DHCP Server** for dynamic IP address assignment
- **RAS/NAT** for routing internal lab traffic to external networks
- **RBAC model** implemented via AD groups and GPOs
- **Lab Clients** (Windows/Linux VMs) joined to domain and routed through NAT
- **Virtualization Layer** Proxmox

![Architecture Diagram](./img/ws2019-adds-ras-dhcp.png)

---

## 🔧 Tools & Technologies

- Windows Server 2019 Standard
- Active Directory Domain Services (ADDS)
- DHCP Server Role
- Remote Access Services (RAS) with NAT
- Group Policy Management Console (GPMC)
- Proxmox VE

---

## 🧠 Role-Based Access Control (RBAC)

| Role            | Permissions                                      |
|-----------------|--------------------------------------------------|
| Domain Admins   | Full control of ADDS, DHCP, and RAS/NAT config   |
| Helpdesk        | Password resets, account unlocks, DHCP leases    |
| Standard Users  | Domain login, DHCP IP assignment, NAT access     |
| Guests          | Internet-only access via NAT, no domain join     |

---

## ⚡ Setup Highlights

1. **Install ADDS** and promote server to domain controller.
2. **Configure DHCP scopes** aligned with domain subnet.
3. **Enable RAS/NAT** to route traffic from lab clients.
4. **Create AD groups** and apply GPOs for RBAC enforcement.
5. **Join lab clients** to domain and verify DHCP/NAT functionality.

---

## 🚀 Outcome

This lab delivers a fully functional Windows Server 2019 environment with ADDS, DHCP, and NAT services. It enables realistic testing of group policies, RBAC, and secure network design — all within a home network. Ideal for cybersecurity practice, IAM workflows, and infrastructure experimentation.

---

## 📂 Resources

- [Microsoft Docs — ADDS on Windows Server 2019](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/windows-server-2019)
- [Proxmox VE](https://www.proxmox.com/en/)
- [TheOldTek Website](https://aguirluis.github.io/theoldtek)

---

## 🧑‍💻 Author

**Luis E. Aguirre**  
System Admin • Cybersecurity • Home Network Architect  
🔗 [LinkedIn](https://linkedin.com/in/luis-aguirre01)  
📧 aguirluis@gmail.com  
