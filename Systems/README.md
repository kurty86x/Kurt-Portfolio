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
- Configured persistent mounts in `/etc/fstab`  
- Performed live filesystem expansion using `lvextend` and `resize2fs`  
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
Built a multi‑VM environment using VirtualBox and Hyper‑V for testing and rollback scenarios.

**Key Work:**  
- Created isolated test networks  
- Used snapshots for rollback testing  
- Compared Type 1 vs Type 2 hypervisors  
- Benchmarked VM performance 

**Documentation:**  
- [`virtualization-notes.md`](virtualization-notes.md)

---

