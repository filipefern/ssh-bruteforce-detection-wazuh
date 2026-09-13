# ssh-bruteforce-detection-wazuh

SSH brute-force detection lab using Wazuh SIEM

## Overview

This is a Blue Team cybersecurity lab project where I build a detection and response workflow for SSH brute-force attacks using Wazuh SIEM. The goal is to gain hands-on experience in alert triage, log analysis, and incident response in a controlled environment.

## Objective

Design, implement, and document a complete incident detection and response cycle:
- Detect SSH brute-force attempts in real time using Wazuh
- Investigate security events through the SIEM dashboard and log analysis
- Create custom detection rules based on attack patterns
- Implement automated response (IP blocking with fail2ban)
- Document the entire incident lifecycle with evidence and findings

## Architecture

```
Kali Linux (Attacker)
    └─ SSH brute-force attack with Hydra
        └─ Target: ubuntu.server

Ubuntu Server 26.04.1 LTS (Victim)
    └─ SSH service (target)
    └─ Wazuh Agent (log collection)
        └─ Sends logs to the Manager

Wazuh Manager (SIEM)
    └─ Receives and analyzes logs
    └─ Applies detection rules
    └─ Generates alerts
    └─ Dashboard for visualization

SOC Analyst (Investigation)
    └─ Alert triage
    └─ Log analysis
    └─ Incident response
    └─ Automated blocking
```

## Technology Stack

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| Virtualization | VMware Workstation Pro | 7.x | VM hosting |
| Target System | Ubuntu Server | 26.04.1 LTS | SSH victim machine |
| SIEM | Wazuh | 4.14.7 | Log collection, detection, and analysis |
| Attack Tool | Kali Linux + Hydra | Latest | SSH brute-force simulation |
| Response Tool | fail2ban | Latest | Automated IP blocking |

## Lab Progress

### Phase 1: Infrastructure Setup
- [x] Installation and configuration of VMware Workstation Pro
- [x] Deployment of Ubuntu Server 24.04 VM
- [x] Installation of Wazuh Manager (all-in-one appliance)
- [x] Installation and registration of Wazuh Agent (Agent ID: 001)
- [x] Agent-Manager connectivity validation (Status: Active)
- [x] Network configuration (bridged network)
- [x] Deployment of Kali Linux VM
- [x] Network connectivity verification between the three VMs

### Phase 2: Attack Execution
- [x] Installation of Hydra on Kali Linux
- [x] Wordlist preparation for the brute-force attack
- [x] Execution of the SSH brute-force attack (duration: 16 minutes)
- [x] Event capture and ingestion into the SIEM

### Phase 3: Investigation & Analysis
- [x] Review of alerts on the Wazuh dashboard
- [x] Log analysis and pattern identification
- [x] Attack timeline reconstruction (source IP, attempt count, timing)
- [x] Evidence collection (screenshots, logs)
- [x] Documentation of attack characteristics

### Phase 4: Response & Remediation
- [x] Creation/tuning of a custom detection rule
- [x] Alert severity configuration
- [x] Automated response setup (fail2ban integration)
- [x] Validation that the attack was detected and blocked

### Phase 5: Documentation & Reporting
- [x] Incident report generation
- [x] Summary of findings and analysis
- [x] Lessons learned documentation
- [x] Final review of the lab and GitHub documentation

## VM Specifications

### Ubuntu Server (Target/Victim)

```
RAM: 2 GB
Processors: 2
Disk: 20 GB
OS: Ubuntu Server 26.04.1 LTS
Interface: Terminal (no GUI)
Network: Bridged
Services: SSH, Wazuh Agent
```

### Wazuh Manager (SIEM)

```
RAM: 8 GB
Processors: 4
Disk: 50 GB
Network: Bridged
Dashboard: HTTPS on port 443
Components: Manager, Indexer, Dashboard
```

### Kali Linux (Attacker)

```
RAM: 2 GB
Processors: 2
Disk: 30 GB
Interface: Desktop GUI
Network: Bridged
Tools: Hydra, standard penetration testing tools
```

## Prerequisites

- PC/Laptop with a minimum of 16 GB RAM
- 80 GB of free disk space
- VMware Workstation Pro installed and working
- 4-6 hours for the full lab execution

## Installation & Setup

1. **VMware Workstation Pro Installation** - Download and install VMware Workstation Pro
2. **Ubuntu Server Setup** - Create the VM with the specifications above, enable SSH
3. **Wazuh Manager** - Deploy using the OVA appliance, note the access credentials
4. **Wazuh Agent** - Install the agent on Ubuntu, register it with the manager
5. **Kali Linux** - Create the VM with a desktop environment, install Hydra
6. **Network Configuration** - Ensure the three VMs can communicate over the bridged network
7. **Attack Execution** - Run Hydra against the target SSH service
8. **Investigation** - Access the Wazuh dashboard and analyze the generated alerts

## Key Findings

- SSH brute-force attack detected in real time
- A total of 1021 login attempts were captured
- No successful logins (password not compromised)
- Attack pattern correctly mapped to MITRE T1110.001 (Brute Force)
- Automated fail2ban response worked, blocking subsequent attempts

## Lessons Learned

- SSH on port 22 is vulnerable to brute-force attacks
- SIEM-based detection is effective (the attack was captured in real time)
- Automated response (fail2ban) prevents a successful compromise
- Analyzing event logs with close attention to detail is crucial so no information is missed
- Ensuring the correct implementation of preventive and corrective access controls, such as fail2ban, is essential
- Recommendation: implement key-based authentication instead of password authentication
- Documentation and forensic analysis are critical to understanding the incident

## References

- [Official Wazuh Documentation](https://documentation.wazuh.com/)
- [MITRE ATT&CK Framework - Brute Force (T1110)](https://attack.mitre.org/techniques/T1110/)
- [Hydra Documentation](https://www.kali.org/tools/hydra/)
- [fail2ban Documentation](https://fail2ban.readthedocs.io/en/latest/)
- [CIS Benchmarks](https://www.cisecurity.org/)

## Important Notes

- **Educational Purpose**: This lab is designed for learning cybersecurity concepts in a controlled environment
- **No Real Data**: No real or sensitive data is used in this lab
- **Legal**: This simulation is intended solely for authorized security training

## Lab Status

- **Started**: September 5, 2026
- **Completed**: September 12, 2026
- **Current Phase**: 5 (Completed)
- **Last Updated**: September 12, 2026

---

**Author**: Filipe Fernandes
**Purpose**: Building Blue Team / SOC Analyst experience
