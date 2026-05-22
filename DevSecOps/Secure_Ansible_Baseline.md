# 📝 Overview
This project demonstrates how I used Ansible to automate secure configuration tasks on Linux servers. The goal was to learn how configuration management tools help enforce consistency, reduce manual work, and apply basic security settings across multiple systems.

---

### 🎯 Objectives
- Automate common Linux configuration tasks
- Apply beginner‑level security settings using Ansible
- Learn how inventories, playbooks, and roles work
- Validate changes across multiple lab VMs
- Practice idempotent automation (safe to run repeatedly)

---

### 🏗️ Lab Environment
- 1 Ansible control node (RHEL)
- 2–3 Linux target VMs
- SSH key‑based authentication
- Python + Ansible installed

---

### 📁 Project Structure
```Folder Structure
ansible-secure-baseline/ 
│── inventory 
│── playbooks/ 
│     └── secure_baseline.yml 
│── roles/ 
│     └── baseline/ 
│           ├── tasks/main.yml 
│           ├── templates/ 
│           └── handlers/main.yml 
└── docs/ 
```

---

# 🔐 Key Security Tasks Automated (yaml)

### 1. Enforce SSH Key Authentication
```yaml
- name: Disable password authentication
  lineinfile:
    path: /etc/ssh/sshd_config
    regexp: '^PasswordAuthentication'
    line: 'PasswordAuthentication no'
```
### 2. Disable Root Login
```yaml
- name: Disable root SSH login
  lineinfile:
    path: /etc/ssh/sshd_config
    regexp: '^PermitRootLogin'
    line: 'PermitRootLogin no'
```

### 3. Remove Unnecessary Packages
```yaml
- name: Remove unused packages
  package:
    name: ['telnet', 'rsh', 'ftp']
    state: absent
```

---

## ▶️ Running the Playbook
```
ansible-playbook -i inventory playbooks/secure_baseline.yml
```

---

## 🧪 Validation Steps
- SSH password login disabled
- Root login disabled
- Unnecessary packages removed
- Firewall running and enabled
- Sensitive files have correct permissions

---

## 🛠️ Troubleshooting
- SSH lockout → Use console access to revert sshd_config
- Playbook fails → Run with -vvv for verbose output
- Permissions not applying → Check for conflicting distro defaults

---

## 📘 What I Learned
- How to structure an Ansible project
- How to automate secure configuration tasks
- How to validate changes across multiple systems
- How automation supports DevSecOps practices

---