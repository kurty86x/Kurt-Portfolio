# 🖥️ Linux and Systems Administration Portfolio

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

### 1. Linux Server Administration  
<img src="Images/linux_server.png" width="420">

**Summary:**  
Built and hardened RHEL Servers following best practices. Performed core Linux administration tasks across security, storage, and monitoring.

**Key Work:**  
- Configured SSH key authentication  
- Disabled password login & root login  
- Filesystems,LVM and disk monitoring  
- Automated updates with `unattended-upgrades`  
- Created monitoring scripts for CPU, RAM, and disk  

**Documentation:**  
- [`linux-hardening`](linux-hardening.md)
- [`ansible-automation`](ansible-automation.md)

---

### 2. Linux Storage, Filesystems & LVM Administration  
<img src="Images/storage.png" width="420">

**Summary:**  
Designed and implemented Linux storage solutions using partitions, filesystems, and Logical Volume Management (LVM). Automated monitoring and performed live volume resizing.

**Key Work:**  
- Partitioned disks using `fdisk` and `parted`  
- Created and managed LVM (PV → VG → LV)  
- Formatted and mounted filesystems (ext4, XFS)   
- Performed live filesystem expansion using `lvextend`, `resize2fs` and  `xfs_growfs` 
- Implemented disk‑usage monitoring and SMART health checks  
- Automated cleanup of logs, temp files, and stale data  

**Documentation:**  
- [`lvm-provisioning`](lvm-provisioning.md)  
- [`disk-monitoring`](disk-monitoring.md)  


---

### 3. Windows Server Administration + Active Directory  
<img src="Images/ad_diagram.png" width="420">

**Summary:**  
Deployed a Windows Server 2022 domain controller and configured core identity services.

**Key Work:**  
- Installed and configured AD DS  
- Set up DNS & DHCP  
- Created OU structure and Group Policies  
- Automated user creation with PowerShell  
- Implemented login scripts and drive mappings  


**Documentation:**  
- [`Domain Controller build`](adbuild.md)

---

### 4. Virtualization & Snapshots Lab  
<img src="Images/virtualization.png" width="420">

**Summary:**  
Used VMware in a production environment to run and manage virtual machines for daily system administration tasks. Performed basic VM provisioning, maintenance, and snapshot management to support server operations and testing.

**Key Work:**  
- Created and managed VMs in VMware (production environment)  
- Performed basic VM provisioning (CPU, RAM, disk, ISO mounting)  
- Used snapshots before updates or configuration changes  
- Expanded virtual disks and adjusted VM resources when needed  
- Managed VM power operations (start, stop, restart)  
- Connected VMs to existing production networks  
- Assisted with troubleshooting VM performance or connectivity issues  

**Documentation:**  
- [`virtualization-notes.md`](virtualization-notes.md)

---

