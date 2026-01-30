# SOC Home Lab – Network Reconnaissance Detection

## Overview
This project demonstrates a Security Operations Center (SOC) detection workflow by simulating network reconnaissance activity from a Kali Linux machine and analyzing how it is detected and blocked by native Windows security controls on a Windows 10 system.

---

## Lab Environment

### Attacker System
- Operating System: Kali Linux (Rolling)
- Role: Internal attacker
- Tools Used: Nmap, Ping

### Target System
- Operating System: Windows 10 x64
- Role: Defender
- Security Controls:
  - Windows Defender Firewall
  - Windows Filtering Platform
  - Advanced Audit Policy Configuration

---

## Attack Scenario
The attacker system performed network reconnaissance including:
- ICMP reachability checks
- TCP SYN scanning
- Service enumeration
- OS detection attempts

These actions represent early-stage attacker behavior and were blocked by the Windows Defender Firewall.

---

## Evidence Collected

### Attacker-side (Kali Linux)
- Nmap scan output
- Ping and TCP probe activity
- Reconnaissance logs captured during the attack phase

### Defender-side (Windows 10)
- Windows Defender Firewall logs
- Windows Security Event Viewer logs
- Event ID 5157 (Blocked connection – Windows Filtering Platform)

---

## Detection Analysis
From a SOC analyst perspective, the observed activity is classified as **network reconnaissance**.

Key indicators:
- Multiple inbound TCP connection attempts
- Single source targeting multiple ports in a short time window
- Connections blocked before session establishment

Windows Defender Firewall successfully blocked all unsolicited inbound traffic. Event ID 5157 confirms enforcement at the Windows Filtering Platform layer, indicating effective host-based protection.

---

## MITRE ATT&CK Mapping
- **Tactic:** Reconnaissance (TA0043)
- **Technique:** Active Scanning

---

## SOC Skills Demonstrated
- Network reconnaissance detection
- Firewall log analysis
- Windows Event Viewer investigation
- Audit policy configuration
- Attacker–defender log correlation
- Log sanitization and documentation
- SOC-style reporting

---

## Future Enhancements
- Forward logs to a SIEM platform
- Deploy Sysmon for deeper visibility
- Simulate authentication attacks
- Create detection rules and alerts
- Expand to multi-stage attack scenarios

---

## Disclaimer
This lab was conducted strictly for educational purposes within a controlled virtual environment. No production systems or real networks were targeted.
