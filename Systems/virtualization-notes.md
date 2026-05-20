```markdown
# VMware Virtualization Notes

## Overview
These notes cover the VMware tasks I perform in a production environment as part of my system administration responsibilities. This includes creating VMs, managing resources, using snapshots, and performing basic troubleshooting.

---

## VMware Tasks I Perform
- Creating new VMs for Linux and Windows Server  
- Assigning CPU, RAM, and storage based on requirements  
- Mounting ISO files for OS installation  
- Managing VM power operations (start, stop, restart)  
- Taking snapshots before updates or configuration changes  
- Reverting snapshots if issues occur  
- Expanding virtual disks when servers need more space  
- Connecting VMs to the correct production networks  
- Checking VM performance (CPU, RAM, disk usage)  

---

## Networking
In production, I typically work with:
- **Production VLANs**  
- **Management networks**  
- **Standard vSwitch or distributed switch (depending on environment)**  

My tasks include:
- Ensuring VMs are connected to the correct port group  
- Verifying network connectivity after provisioning  

---

## Snapshots
Snapshots are used for:
- Pre‑update safety  
- Testing configuration changes  
- Quick rollback if something breaks  

Snapshot workflow:
1. Take snapshot  
2. Apply update or change  
3. Validate  
4. Roll back if needed  

---

## Resource Adjustments
Tasks I’ve performed:
- Increasing VM RAM or CPU  
- Expanding virtual disks (VMDKs)  
- Coordinating with storage or virtualization teams when required  

---

## Troubleshooting
Common issues I help resolve:
- VM not powering on  
- Network connectivity problems  
- High CPU or RAM usage  
- Disk space alerts  
- VMware Tools not running  

---

## Summary
I use VMware as part of my daily system administration work to manage virtual machines, perform updates safely, and support production operations. My responsibilities focus on practical, real‑world VM management rather than advanced VMware engineering.