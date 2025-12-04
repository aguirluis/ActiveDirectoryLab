# 📝 Standard Operating Procedure (SOP)  
## Windows Server 2019 — ADDS + RAS/NAT + DHCP (Single Scope)

This SOP outlines the steps to deploy a Windows Server 2019 Domain Controller with **Active Directory Domain Services (ADDS)**, **Dynamic Host Configuration Protocol (DHCP)**, and **Remote Access Services (RAS/NAT)**.

---

## 1. Pre‑Installation
- Install Windows Server 2019 Standard (VM or physical).
- Assign **static IP** to internal NIC: `172.16.0.1`.
- Configure external NIC for internet access.
- Rename server (e.g., `DC01`).
- Apply latest Windows updates.

---

## 2. Active Directory Domain Services (ADDS)
1. Open **Server Manager → Add Roles and Features**.
2. Select **Active Directory Domain Services**.
3. After installation, click **Promote this server to a domain controller**.
4. Choose **Add a new forest** → Domain: `mydomain.local`.
5. Configure DNS delegation if prompted.
6. Set **DSRM password**.
7. Restart server after promotion.
8. Verify domain functionality by joining a test client.

---

## 3. DHCP Configuration
1. In **Server Manager → Add Roles and Features**, select **DHCP Server**.
2. After installation, open **DHCP Console**.
3. Create a **new scope**:
   - Name: `LAN-Scope`
   - IP Range: `172.16.0.100 – 172.16.0.200`
   - Subnet Mask: `255.255.255.0`
   - Default Gateway: `172.16.0.1`
   - DNS Server: `172.16.0.1`
4. Activate scope.
5. Authorize DHCP server in ADDS.
6. Test by connecting a client → verify IP lease.

---

## 4. RAS/NAT Setup
1. In **Server Manager → Add Roles and Features**, select **Remote Access**.
2. Choose **Routing** role service.
3. Open **Routing and Remote Access (RRAS)** console.
4. Right‑click server → **Configure and Enable Routing and Remote Access**.
5. Select **Network Address Translation (NAT)**.
6. Configure:
   - External NIC → Public/Internet connection.
   - Internal NIC (`172.16.0.1`) → Private LAN.
7. Start RRAS service.
8. Test internet access from a client.

---

## 5. Validation
- **ADDS**: Client joins domain, user logon works.
- **DHCP**: Client receives IP from scope.
- **NAT**: Client browses internet via DC.
- **DNS**: Client resolves domain names through DC.

---

## 6. Documentation & Maintenance
- Record IP ranges, domain details, and role configurations.
- Apply **Group Policies** for security.
- Schedule backups for ADDS and DHCP.
- Monitor RRAS logs for connectivity issues.

---

✅ Following this SOP ensures a repeatable and reliable deployment of a Windows Server 2019 lab environment with ADDS, DHCP, and NAT services.
