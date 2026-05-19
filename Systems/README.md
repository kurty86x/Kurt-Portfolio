# 🖥️ Systems Administration Portfolio

This section highlights my hands‑on experience with Linux, Windows Server, virtualization, automation, and core system administration practices. Each project includes documentation, screenshots, and configuration steps.

---

## 🔧 Core Systems Skills

- Linux administration (users, permissions, services, SSH)
- Windows Server (AD DS, DNS, DHCP, Group Policy)
- Virtualization (Hyper‑V, VirtualBox)
- Bash & PowerShell scripting
- System hardening & patching
- Monitoring & troubleshooting (logs, performance tools)
- Basic networking required for system functionality (DNS, ports, firewalls)

---

## 🗂️ Projects

### 1. Linux Server Build & Hardening  
<img src="Images/linux_server.png" width="420">

**Summary:**  
Built and hardened RHEL Servers following best practices.

**Key Work:**  
- Configured SSH key authentication  
- Disabled password login & root login  
- Set up UFW firewall rules  
- Automated updates with `unattended-upgrades`  
- Created monitoring scripts for CPU, RAM, and disk  

**Documentation:**  
- [`linux-hardening`](linux-hardening.md)
- [`ansible-automation`](ansible-automation.md)

---

### 2. Windows Server + Active Directory Lab  
<img src="Images/ad_diagram.png" width="420">

**Summary:**  
Deployed a Windows Server 2022 domain controller in a virtual lab.

**Key Work:**  
- Installed and configured AD DS  
- Set up DNS & DHCP  
- Created OU structure and Group Policies  
- Automated user creation with PowerShell  
- Implemented login scripts and drive mappings  

**Documentation:**  
- [`ad-lab-setup.md`](ad-lab-setup.md)

---

### 3. Virtualization & Snapshots Lab  
<img src="Images/virtualization.png" width="420">

**Summary:**  
Built a multi‑VM environment using VirtualBox and Hyper‑V.

**Key Work:**  
- Created isolated test networks  
- Used snapshots for rollback testing  
- Compared Type 1 vs Type 2 hypervisors  
- Benchmarked VM performance  

**Documentation:**  
- [`virtualization-notes.md`](virtualization-notes.md)

---

## 📁 Folder Structure