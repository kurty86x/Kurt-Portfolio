# 🔐 Linux Server Hardening & Automation Project

This project demonstrates my ability to secure a Linux server using industry best practices and automation. I implemented multiple hardening steps and created scripts to enforce security controls consistently across systems.

---

## 🧩 Objectives

- Reduce attack surface  
- Enforce secure authentication  
- Automate repetitive security tasks  
- Improve system monitoring  
- Follow CIS‑style hardening principles  

---

## 🛠️ Hardening Steps Implemented

### 🔑 SSH Security
- Disabled root login  
- Disabled password authentication  
- Enforced SSH key authentication  
- Changed default SSH port  


### 🔥 Firewall Configuration
- Enabled UFW  
- Allowed only required ports  
- Denied all inbound by default  

### 👤 User & Permission Hardening
- Created non‑root admin user  
- Added user to sudoers  
- Audited file permissions  
- Removed unused packages  

### 🔄 Automatic Updates
- Enabled `unattended-upgrades`  
- Configured automatic security patches  

### 📊 Monitoring & Logging
- Created scripts to monitor CPU, RAM, disk  
- Configured log rotation  
- Enabled audit logging  

---

## 📜 Automation Scripts

### System Monitoring Script
```bash
#!/bin/bash
echo "===== System Resource Report ====="
echo "CPU Load:"
uptime
echo "Memory Usage:"
free -h
echo "Disk Usage:"
df -h
```
### SSH Hardening Script
```bash
#!/bin/bash

##### This Script is to remediate SSH Secure Configs for Linux.

# Path to sshd_config
SSHD_CONFIG="/etc/ssh/sshd_config"
BACKUP="/etc/ssh/sshd_config.bak"

# Check for root privileges
if [ "$EUID" -ne 0 ]; then
  echo "Please run as root."
  exit 1
fi

# Backup the original file
cp "$SSHD_CONFIG" "$BACKUP"
echo "Backup created at $BACKUP"

# Function to update or add a config line, including uncommenting
update_config() {
  KEY="$1"
  VALUE="$2"
  if grep -Eq "^\s*#?\s*$KEY\b" "$SSHD_CONFIG"; then
    sed -i "s|^\s*#\?\s*$KEY\b.*|$KEY $VALUE|" "$SSHD_CONFIG"
  else
    echo "$KEY $VALUE" >> "$SSHD_CONFIG"
  fi
  echo "Set $KEY to $VALUE"
}

# Secure SSH configurations
update_config "PermitRootLogin" "no"  
update_config "PasswordAuthentication" "yes"
update_config "X11Forwarding" "no"
update_config "AllowTcpForwarding" "no"
update_config "LogLevel" "INFO"
update_config "MaxAuthTries" "4"
update_config "MaxSessions" "4"
update_config "IgnoreRhosts" "yes"
update_config "HostbasedAuthentication" "no"
update_config "PermitEmptyPasswords" "no"
update_config "PermitUserEnvironment" "no"
update_config "ClientAliveInterval" "300"
update_config "ClientAliveCountMax" "0"
update_config "LoginGraceTime" "60"
update_config "MaxStartups" "10:30:60"
update_config "Protocol" "2"
update_config "PubkeyAuthentication" "yes"
update_config "ChallengeResponseAuthentication" "no"

# Restart SSH service
systemctl restart sshd && echo "SSH service restarted successfully."
```