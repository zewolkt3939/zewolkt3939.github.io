---
layout: page
permalink: /roadmap/
title: roadmap
description: What I’m leveling next — networking, Linux, AppSec, SOC/detection, AI for security — with clear priorities for hiring conversations.
nav: true
nav_order: 3
---

This page is my **public learning backlog**, not a course catalog. It answers: *what is Bao improving next, and how does it connect to the roles he wants?*

## Target roles

Security Engineer · AI Security Engineer · SOC / detection engineering · AppSec-adjacent junior roles · security-minded infrastructure

## Learning path (order I still follow)

1. **Foundation** — Linux daily ops + network fundamentals (CCNA track, ~80%).  
2. **Lab building** — Docker/VMware environments that can be torn down and rebuilt.  
3. **Application security** — PortSwigger + real plugin review habits from Fore-Z.  
4. **Cloud** — AWS identity, network controls, host baseline.  
5. **Defensive ops** — SIEM workflows, triage, investigation notes.  
6. **AI-assisted security** — alert prioritization, malware analysis assist, analyst UX (evidence first).

## Current priorities (this quarter)

1. Finish remaining **CCNA** depth with packet-level validation, not flashcards only.  
2. Keep **Linux firewall / packet tooling** sharp after the LG DUT internship.  
3. Expand **AppSec** notes into interview-ready story banks (authZ, injection, session).  
4. Harden **AI-APW / malware platform** narratives: architecture, limits, next metrics.  
5. Grow **cloud security** scenarios on AWS (IAM + SG + logging story).

## Topic map

### Networking (CCNA)

OSI, TCP/IP, VLANs, inter-VLAN routing, STP/RSTP, EtherChannel, OSPF, NAT, ACL, DHCP, DNS, QoS, SNMP, subnetting, VLSM, DMZ, segmentation.

### Linux & host security

Bash, SSH, permissions, systemd, packages, storage, services, iptables/nftables, Docker, baseline hardening — including automotive/webOS-oriented constraints from internship work.

### Application security

OWASP-oriented labs, Burp Suite workflows, WordPress/PHP review patterns, authentication and authorization failures.

### Cloud (AWS)

EC2, IAM, VPC, Security Groups, Elastic IP, shared-responsibility model, least privilege.

### SOC / detection

Wazuh, Elastic concepts, Suricata, pfSense lab topologies, alert triage, MITRE ATT&CK mapping, notification quality.

### AI for security

LLM-assisted triage with guardrails, malware feature pipelines, structured reports for humans — never silent drop of critical events.

## Evidence already on this site

| Priority theme | Where to look |
| -------------- | ------------- |
| SIEM + automation | [AI-APW]({{ '/projects/10_ai_apw/' | relative_url }}) |
| Malware analysis | [Platform project]({{ '/projects/02_malware_analysis/' | relative_url }}) |
| Embedded/Linux security | [LG DUT internship]({{ '/projects/03_automotive_cybersecurity/' | relative_url }}) |
| AppSec research | [Fore-Z]({{ '/projects/04_wordpress_security_research/' | relative_url }}) |
| Lab ops | [Home lab]({{ '/projects/05_security_home_lab/' | relative_url }}) |
| Full timeline | [CV + PDF]({{ '/cv/' | relative_url }}) |
