# linux-server-hardening-lab
Documentation of an Ubuntu Server hardening lab including SSH security, firewall configuration, and Fail2ban intrusion prevention.
# Linux Server Hardening & Fail2ban Security Lab

## Overview
This project documents the deployment and security hardening of an Ubuntu Server
virtual machine. The primary goal was to configure secure remote access, reduce
the server’s attack surface, and implement automated intrusion prevention for
SSH access using Fail2ban.

This lab was built to develop practical Linux system administration and
cybersecurity skills, including service management, authentication hardening,
log analysis, and troubleshooting.

---

## Environment
- Host Operating System: Windows 11
- Virtualization Platform: VirtualBox
- Server Operating System: Ubuntu Server
- Remote Access Method: SSH
- Firewall: UFW (Uncomplicated Firewall)
- Intrusion Prevention: Fail2ban

---

## SSH Hardening
The server was secured to follow common industry best practices for remote
administration:

- Configured SSH key-based authentication
- Disabled password-based SSH authentication
- Disabled root SSH login
- Verified effective runtime configuration using `sshd -T`
- Managed the server remotely from a Windows client via SSH

These changes significantly reduce the risk of brute-force attacks and
unauthorized access.

---

## Firewall Configuration
Host-based firewall rules were implemented using UFW to restrict network access:

- Enabled UFW firewall
- Allowed SSH traffic explicitly
- Denied all other inbound connections by default

This ensures only required services are exposed to the network.

---

## Fail2ban Intrusion Prevention
Fail2ban was installed and configured to automatically detect and block repeated
failed SSH login attempts.

### SSH Jail Configuration
- Monitors SSH authentication logs
- Bans IP addresses after repeated failed login attempts
- Applies temporary bans to reduce attack impact

Key configuration values:
- Maximum retries: 5
- Detection window: 10 minutes
- Ban duration: 30 minutes

---

## Verification & Monitoring
The following methods were used to verify proper operation and security:

- Confirmed Fail2ban service status using `systemctl`
- Verified active SSH protection using `fail2ban-client status sshd`
- Reviewed SSH authentication logs using `journalctl`
- Troubleshot and resolved Fail2ban startup errors caused by duplicate jail
  definitions

---

## Learning Outcomes
Through this project, I gained hands-on experience with:

- Linux server deployment and administration
- SSH authentication mechanisms and hardening techniques
- Firewall configuration and access control
- Log analysis and service troubleshooting
- Automated intrusion prevention using Fail2ban
- Writing clear technical documentation for security-related systems

---

## Notes
This repository contains documentation only. No sensitive information such as
IP addresses, credentials, or SSH keys are included.
