# Securing Linux Servers Using Honeypots and IP Blocking

## 📌 Overview

This project demonstrates a practical approach to securing Linux servers against SSH brute-force attacks through the deployment of a honeypot, SSH hardening techniques, automated log monitoring, and dynamic IP blocking.

The solution was designed to detect, analyze, and mitigate malicious SSH login attempts on a public-facing Linux server. By combining defensive security controls with automation, the project provides real-time threat detection and proactive response capabilities.

---

## 🎯 Objective

To deploy a honeypot and configure defensive mechanisms such as SSH hardening and automated IP blocking to detect, analyze, and mitigate SSH brute-force attacks on public-facing Linux servers.

---

## 🏗️ Project Architecture

```text
                +-------------------+
                |   Attacker VM     |
                |   (Kali Linux)    |
                +---------+---------+
                          |
                          |
                    SSH Attack
                          |
                          v
              +----------------------+
              |   Honeypot Server    |
              |      CentOS VM       |
              +----------------------+
               |        |        |
               |        |        |
         Apache      SSH      Firewall
         Reports   Hardened   Protection
               |
               v
     Log Monitoring Scripts
               |
               v
      Automated IP Blocking
               |
               v
      Security Reports Generated
```

---

## 🛠️ Technologies Used

### Operating Systems
- CentOS Linux
- Kali Linux

### Services
- OpenSSH
- Apache HTTP Server
- VSFTPD

### Security Components
- SELinux
- Firewalld
- Honeypot Environment

### Automation & Scripting
- Bash Shell Scripting
- Cron Jobs

### Monitoring & Analysis
- Linux Log Analysis
- Whois Lookup
- IP Tracking

---

## 🔐 Security Controls Implemented

### SSH Hardening

- Changed the default SSH port from **22** to **2222**
- Updated SELinux policies to allow the custom SSH port
- Restarted and validated SSH services

**Benefits**
- Reduces automated attack noise
- Minimizes exposure to common SSH scans
- Improves server security posture

---

### Firewall-Based Protection

Implemented dynamic IP blocking using Firewalld.

**Features**
- Detects repeated failed SSH login attempts
- Automatically blocks malicious IP addresses
- Creates permanent firewall rules
- Reloads firewall configurations automatically

Example:

```bash
firewall-cmd --permanent \
--add-rich-rule="rule family='ipv4' source address='ATTACKER_IP' reject"

firewall-cmd --reload
```

---

### Log Monitoring & Threat Detection

The solution continuously monitors Linux authentication logs.

**Monitored Files**

```bash
/var/log/secure
/var/log/secure*
```

**Extracted Information**
- Attacker IP Address
- Failed Login Attempts
- Attack Frequency
- Country of Origin
- Security Events

---

## ⚙️ Automation Scripts

### 1. b_track_ssh_daily

**Purpose**
- Parses SSH authentication logs
- Extracts attacker IP addresses
- Performs Whois lookups
- Generates attacker reports
- Saves findings for analysis


### 2. protect_ssh

**Purpose**
- Detects brute-force attacks
- Counts failed SSH login attempts
- Automatically blocks malicious IPs
- Updates firewall rules

**Features**
- Automated threat mitigation
- Reduced manual intervention
- Improved server protection

---

## 📊 Workflow

```text
SSH Attack Attempt
        │
        ▼
Authentication Failure Logged
        │
        ▼
Log Monitoring Script Runs
        │
        ▼
Attacker IP Identified
        │
        ▼
Failed Attempts Counted
        │
        ▼
Threshold Reached?
        │
   ┌────┴────┐
   │         │
  No        Yes
   │         │
   ▼         ▼
Monitor   Block IP
              │
              ▼
Generate Report
```

---

## 📈 Results

### Successfully Achieved

✅ Honeypot deployment on a Linux server

✅ Detection of SSH brute-force attacks

✅ Automated log monitoring

✅ Attacker IP identification

✅ Country-based attacker analysis

✅ Automated IP blocking

✅ Firewall-based threat mitigation

✅ Security report generation

---

## 📂 Sample Security Report

Generated reports contain:

- Attacker IP addresses
- Number of failed login attempts
- Whois information
- Country of origin
- Security event summaries

Example:

```text
IP Address: xxx.xxx.xxx.xxx
Country: Example Country
Failed Attempts: 15
Status: Blocked
```

## Honeypot Environment

- Virtual machine setup and network configuration.

---

## 🔍 Key Cybersecurity Concepts Demonstrated

- SSH Hardening
- Honeypot Deployment
- Threat Detection
- Intrusion Prevention
- Firewall Management
- Security Automation
- Bash Scripting

---

## 🚀 Future Enhancements

- Integrate Fail2Ban for advanced attack mitigation
- Implement SIEM integration (Splunk / ELK Stack)
- Configure real-time email alerts
- Integrate threat intelligence feeds
- Build attacker geolocation dashboards
- Develop automated security reporting
- Deploy advanced honeypots such as Cowrie

---

## 📚 Learning Outcomes

Through this project, I gained practical experience in:

- Linux Server Administration
- Security Automation
- Bash Scripting
- Firewall Configuration
- SSH Security Hardening
- Threat Analysis

---

## 💼 Skills Demonstrated

- Honeypot Deployment
- SSH Hardening
- Firewall Configuration
- Bash Scripting
- Security Monitoring
- Network Security

---

## ⭐ Project Status

**Completed**

This project was developed as a hands-on cybersecurity lab to demonstrate practical techniques for detecting, analyzing, and mitigating SSH brute-force attacks against Linux systems using honeypots, log monitoring, and automated IP blocking.

---

### If you found this project useful, consider giving it a ⭐ on GitHub.
