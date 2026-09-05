# ssh-bruteforce-detection-wazuh
Lab of SSH brute-force detection using Wazuh SIEM
# SSH Brute-Force Detection Lab with Wazuh SIEM

## Overview

This is a Blue Team cybersecurity lab project where I build a detection and response workflow for SSH brute-force attacks using Wazuh SIEM. The objective is to gain hands-on experience in alert triage, log analysis, and incident response in a controlled environment.

## Objective

To design, implement, and document a complete incident detection and response cycle:
- Detect SSH brute-force attempts in real-time using Wazuh
- Investigate security events through SIEM dashboard and log analysis
- Create custom detection rules based on attack patterns
- Implement automated response (IP blocking with fail2ban)
- Document the entire incident lifecycle with evidence and findings

## Architecture

```
Kali Linux (Attacker)
    └─ Hydra SSH brute-force attack
        └─ Target: 192.168.18.160:22

Ubuntu Server 24.04 (Victim)
    └─ SSH service (target)
    └─ Wazuh Agent (logs collection)
        └─ Forwards logs to Manager

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
| Virtualization | VirtualBox | 7.x | VM hosting |
| Target System | Ubuntu Server | 24.04 LTS | SSH victim machine |
| SIEM | Wazuh | 4.14.7 | Log collection, detection, analysis |
| Attack Tool | Kali Linux + Hydra | Latest | SSH brute-force simulation |
| Response Tool | fail2ban | Latest | Automated IP blocking |

## Lab Progress

### Phase 1: Infrastructure Setup
- [x] VirtualBox installation and configuration
- [x] Ubuntu Server 24.04 VM deployment
- [x] Wazuh Manager installation (all-in-one appliance)
- [x] Wazuh Agent installation and registration (Agent ID: 001)
- [x] Agent-to-Manager connectivity validation (Status: Active)
- [x] Network configuration (Host-only network, IP: 192.168.18.160)
- [x] Kali Linux VM deployment
- [x] Network connectivity verification between all three VMs

### Phase 2: Attack Execution
- [x] Hydra installation on Kali Linux
- [x] Wordlist preparation for brute-force
- [x] SSH brute-force attack execution (duration: 5-10 minutes)
- [x] Event capture and SIEM ingestion

### Phase 3: Investigation & Analysis
- [x] Wazuh dashboard alert review
- [x] Log parsing and pattern identification
- [x] Attack timeline reconstruction (IP source, attempt count, timing)
- [x] Evidence collection (screenshots, logs)
- [x] Attack characteristics documentation

### Phase 4: Response & Remediation
- [ ] Custom detection rule creation/tuning
- [ ] Alert severity configuration
- [ ] Automated response setup (fail2ban integration)
- [ ] Validation that attack is detected and blocked

### Phase 5: Documentation & Reporting
- [ ] Incident report generation
- [ ] Key findings and analysis summary
- [ ] Lessons learned documentation
- [ ] Final lab review and GitHub documentation

## VM Specifications

### Ubuntu Server (Target/Victim)
```
RAM: 2 GB
vCPU: 1 core
Disk: 15 GB
OS: Ubuntu Server 24.04 LTS
Interface: Terminal-only (no GUI)
Network: Host-only (192.168.18.160)
Services: SSH, Wazuh Agent
```

### Wazuh Manager (SIEM)
```
RAM: 8 GB
vCPU: 4 cores
Disk: 50 GB (SSD recommended)
Deployment: All-in-one appliance (OVA)
Network: Host-only (192.168.18.x)
Dashboard: HTTPS on port 443
Components: Manager, Indexer, Dashboard
```

### Kali Linux (Attacker)
```
RAM: 2-4 GB
vCPU: 2 cores
Disk: 20-30 GB
Interface: Desktop GUI (Xfce - lightweight)
Network: Host-only (192.168.18.x)
Tools: Hydra, standard penetration testing tools
```

## Prerequisites

- PC/Laptop with minimum 16 GB RAM (32 GB recommended)
- 80 GB free disk space
- VirtualBox installed and working
- 4-6 hours for complete lab execution

## Installation & Setup (Steps in development)

1. **VirtualBox Installation** - Download and install from virtualbox.org
2. **Ubuntu Server Setup** - Create VM with specifications above, enable SSH
3. **Wazuh Manager** - Deploy using OVA appliance, note access credentials
4. **Wazuh Agent** - Install agent on Ubuntu, register with manager
5. **Kali Linux** - Create VM with desktop environment, install Hydra
6. **Network Configuration** - Ensure all three VMs can communicate via host-only network
7. **Attack Execution** - Run Hydra against target SSH service
8. **Investigation** - Access Wazuh dashboard and analyze generated alerts

## Key Findings (To be updated upon completion)

- [Findings and conclusions will be added as lab progresses]

## Lessons Learned (To be updated upon completion)

- [Key learnings and insights will be documented here]

## References

- [Wazuh Official Documentation](https://documentation.wazuh.com/)
- [MITRE ATT&CK Framework - Brute Force (T1110)](https://attack.mitre.org/techniques/T1110/)
- [Hydra Documentation](https://www.kali.org/tools/hydra/)
- [fail2ban Documentation](https://www.fail2ban.org/wiki/index.php/Main_Page)
- [CIS Benchmarks](https://www.cisecurity.org/)

## Important Notes

- **Educational Purpose Only**: This lab is designed for learning cybersecurity concepts in a controlled environment
- **No Real Data**: No real or sensitive data is used in this lab
- **Isolated Environment**: All VMs operate on a host-only network, not exposed to the internet
- **Legal**: This simulation is intended for authorized security training only

## Lab Status

- **Started**: 03/09/2026
- **Current Phase**: 1 (Infrastructure)
- **Last Updated**: 03/09/2026
- **Estimated Completion**: TBD

---

**Author**: Filipe Fernandes  
**Purpose**: Blue Team / SOC Analyst Experience Building  
**License**: MIT
