# 🖥️ Active Directory Enterprise Lab

## 📌 Overview
This project simulates a **corporate-grade Active Directory environment** built on Windows Server 2019.  
It includes multi-domain controllers, DNS/DHCP integration, security policies, and PowerShell automation.  
The goal was to design, deploy, and manage a secure, scalable directory service similar to what is used in enterprise IT environments.  

---

## ⚙️ Features
- **Redundant Domain Controllers** for high availability  
- **Organizational Unit (OU) hierarchy** by departments (HR, IT, Sales)  
- **Group Policy Objects (GPOs)** for:
  - Password & account lockout policies  
  - Software deployment and drive mapping  
  - Desktop restrictions for standard users  
- **PowerShell Automation** to bulk-create users, groups, and apply policies  
- **Active Directory Certificate Services (AD CS)** for secure authentication  
- **DNS & DHCP** configured for dynamic host resolution and IP management  
- **Monitoring & Troubleshooting** with Event Viewer and DNS logs  

---

## 🏗️ Architecture
![Architecture Diagram](architecture-diagram.png)

- **Domain Controllers**: Primary + Backup  
- **DNS/DHCP** integrated for name resolution and IP distribution  
- **Client PCs** joined to the domain  
- **Role-Based Access Control (RBAC)** implemented through groups  

---

## 📂 Project Files
- `scripts/` → PowerShell scripts for automation  
- `screenshots/` → Key setup and configuration screenshots  
- `configs/` → Exported DHCP, DNS, and GPO settings  
- `troubleshooting.md` → Common issues faced & resolutions  

---

## 🚀 Tools & Technologies
- **Windows Server 2019**  
- **Active Directory Domain Services (AD DS)**  
- **DNS & DHCP**  
- **PowerShell**  
- **VMware Workstation / VirtualBox**  
- **Visio / Lucidchart** (for diagramming)  

---

## 🛠️ Example PowerShell Automation
```powershell
# Bulk user creation script
Import-Module ActiveDirectory

For ($i=1; $i -le 50; $i++) {
    New-ADUser -Name "User$i" -SamAccountName "user$i" `
    -AccountPassword (ConvertTo-SecureString "P@ssw0rd123" -AsPlainText -Force) `
    -Enabled $true -Path "OU=IT,DC=corp,DC=lab"
}
