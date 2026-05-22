# FYI: Coming soon! or On the works

# ⭐ Increasing Disk Space on Linux (LVM + VMware)

This guide explains how to increase disk space for an LVM‑managed filesystem on a Linux VM running in VMware.

---

## 🔍 Step 1: Check Current Disk Usage

Run:

```bash
df -h

example output formatted as a table:
| Filesystem                      | Size | Used | Avail | Use% | Mounted on |
|---------------------------------|------|------|-------|------|------------|
| /dev/mapper/vg_varlog-lv_varlog | 5.0G | 5.0G | 20K   | 100% | /var/log   |


## 🔍 Step 2: Identify Which Virtual Disk to Expand
command:  lsblk

This would help you determine which disk in the VMWare to increase

Example: 
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                         8:0    0  100G  0 disk
├─sda1                      8:1    0  600M  0 part
├─sda2                      8:2    0    1G  0 part /boot
└─sda3                      8:3    0 98.4G  0 part
  ├─rhel-root             253:0    0   50G  0 lvm  /
  ├─rhel-swap             253:1    0    4G  0 lvm  [SWAP]
  └─rhel-home             253:5    0 44.5G  0 lvm  /home 
sdb                         8:16   0   20G  0 disk
└─vg_var-lv_var           253:2    0   20G  0 lvm  /var
sdc                         8:32   0    5G  0 disk
└─vg_varlog-lv_varlog     253:3    0    5G  0 lvm  /var/log

From this example:
- /var/log is on sdc
- So you must increase Hard Disk 3 in VMware.

	
## 🖥️ Step 3: Increase Disk Size in VMware
1. Power off the VM (if required by your environment)
2. Right‑click VM → Edit Settings
3. Select Hard Disk 3
4. Increase size (e.g., from 5GB → 10GB)
5. Power VM back on


## 🔄 Step 4: Rescan the Disk in Linux
Command:
echo 1 > /sys/class/block/sdc/device/rescan


## 📦 Step 5: Resize the Physical Volume
pvresize /dev/sdc
or
parted /dev/sdc  - This is the parted method

print to view Parted number
resizepart 1 100%   -> 1 is the parted number
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  5369MB  5368MB  primary  xfs



## 📈 Step 6: Extend the Logical Volume
lvextend -l +100%FREE /dev/vg_varlog/lv_varlog
or
resizepart 1 100%  -> use when using the parted method


## 🧱 Step 7: Grow the Filesystem
Check what file system it uses
df -Th

Type is xfs
xfs_growfs /var/log

Type is ext4	
resize2fs /dev/vg_varlog/lv_varlog

## ✅ Step 8: Verify
df -h
```