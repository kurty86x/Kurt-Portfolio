# 🧰 Ansible Automation for Linux Patching & CIS Hardening

This document outlines how I used **Ansible** to automate Linux patching and apply a targeted CIS hardening control. The goal was to ensure consistent, repeatable security maintenance across multiple servers with minimal manual effort.

---

## 🎯 Objectives

- Automate OS patching across multiple Linux servers  
- Apply a CIS‑aligned hardening control using Ansible  
- Reduce manual maintenance time  
- Ensure consistent configuration across environments  
- Build a foundation for future automation expansion  

---

## 🗂️ Repository Structure
```text
ansible/
├── inventory
├── playbooks/
│   ├── patching.yml
│   └── cis-ssh.yml
└── files/

## 🔄 Automated Patching Playbook  
**Purpose:** Keep systems up‑to‑date with the latest security patches.

```yaml
---
- name: Apply system updates
  hosts: all
  become: yes

  tasks:
    - name: Update package lists
      apt:
        update_cache: yes

    - name: Upgrade all packages
      apt:
        upgrade: dist