# Enterprise-Projects

Production-style lab environments for hands-on security operations, detection engineering, and threat simulation.
---

## What's Inside

Each lab represents a complete, maintainable environment where I practice detection engineering, test security controls, and simulate real-world attack scenarios.

---

## Splunk 101 - SOC Investigation - MyDFIR

[View Project](https://github.com/dgcyberfolio/Enterprise-Projects/blob/main/Splunk%20Capstone%20Project.md)

**What I Built:**
- Splunk Enterprise SIEM environment
- Windows endpoint with Sysmon logging
- Log forwarding and data ingestion pipeline
- Multi-stage cyberattack investigation

**What I Did:**
- Investigated complete attack chain: brute force → persistence → privilege escalation
- Built SPL queries for security event correlation
- Analyzed Sysmon telemetry
- Created investigation timeline with evidence
- Mapped findings to MITRE ATT&CK framework

---

## Active Directory Attack Lab - MyDFIR

[View Project](https://github.com/dgcyberfolio/Enterprise-Projects/blob/main/Active-Directory-Attack-Lab.md)

**What I Built:**
- Multi-VM Active Directory environment in VirtualBox
- Windows Server 2022 Domain Controller with AD DS
- Splunk Enterprise SIEM with Universal Forwarder on all endpoints
- Sysmon deployment using Olaf Hartong community configuration
- Kali Linux attacker machine for offensive operations

**What I Did:**
- Executed RDP brute force attack using Crowbar against domain users
- Detected attack telemetry in Splunk via Event IDs 4625 and 4624
- Installed and ran Atomic Red Team to simulate MITRE ATT&CK techniques
- Identified detection gaps in endpoint visibility
- Mapped all attack activity to the MITRE ATT&CK framework

---

## How I Use These Labs

### Detection Engineering
- Build KQL and SPL queries in sandbox environment
- Test detection rules before suggesting production deployment
- Validate log sources and data ingestion
- Practice query optimization and performance tuning

### Attack Simulation
- Red team techniques mapped to MITRE ATT&CK
- Test defensive controls and monitoring gaps
- Practice incident response procedures
- Validate alert logic and false positive rates

### Skill Development
- Hands-on with enterprise security tools
- Learn by breaking and fixing things
- Document findings like real SOC investigations
- Build portfolio evidence of practical skills

**Skills Demonstrated:** Splunk SPL • Sysmon analysis • Log aggregation • Windows event monitoring • Attack chain reconstruction • Incident reporting • Active Directory administration • Brute force detection • Adversary simulation

**Stack:** Splunk Enterprise • Universal Forwarder • Sysmon • Windows Server • Active Directory • Kali Linux • Crowbar • Atomic Red Team • VirtualBox • SPL
