# 📂 Windows Server 2019 — File Server Setup

This document describes how to deploy and configure a **Windows Server 2019 File Server** in a domain environment (`mydomain.local`). The File Server provides centralized storage, shared folders, and controlled access for domain users.

---

## 🖥️ Server Configuration

- **Hostname:** FS01  
- **IP Address:** 172.16.0.2  
- **DNS:** 172.16.0.1 (Domain Controller)  
- **Domain:** mydomain.local  
- **Role:** File and Storage Services  

---

## 🔧 Installation Steps

### 1. Pre‑Installation
- Deploy Windows Server 2019 (VM or physical).  
- Assign static IP: `172.16.0.2`.  
- Configure DNS to point to Domain Controller (`172.16.0.1`).  
- Rename server to `FS01`.  
- Apply latest updates.

### 2. Domain Join
1. Open **System Properties → Computer Name → Change**.  
2. Enter domain: `mydomain.local`.  
3. Provide domain admin credentials.  
4. Restart server.  
5. Verify domain membership.

### 3. Install File Server Role
1. Open **Server Manager → Add Roles and Features**.  
2. Select **File and Storage Services → File Server**.  
3. Complete installation.

---

## 📁 Shared Folder Configuration

### 1. Create Folder
- Example: `D:\Shares\Users`

### 2. Share Folder
- Right‑click → **Properties → Sharing → Advanced Sharing**.  
- Share name: `Users`.  
- Set permissions:
  - Domain Admins → Full Control  
  - Helpdesk → Modify  
  - Standard Users → Read/Write  
  - Guests → Read‑only or Deny  

### 3. NTFS Permissions
- Use **Security tab** for granular control.  
- Example:
  - Domain Admins → Full Control  
  - User Groups → Modify  
  - Guests → Read‑only  

---

## 🧑‍💻 Group Policy Integration

- Create a GPO to map network drives automatically:  
  - Path: `\\FS01\Users`  
  - Apply to specific AD groups.  

---

## ✅ Validation

- Log in as a domain user.  
- Confirm drive mapping.  
- Test file creation, modification, and access control.  

---

## 🔒 Maintenance & Security

- Monitor disk usage and quotas.  
- Enable **Shadow Copies** for file recovery.  
- Schedule backups.  
- Audit access logs for compliance.  

---

## 🚀 Outcome

The File Server provides centralized storage for domain users, integrated with ADDS authentication and Group Policy. This completes the lab environment with **identity (ADDS)**, **networking (DHCP/NAT)**, and **storage (File Server)**.

