---
layout: page
title: Security Home Lab (Linux, Docker, Network, AWS)
description: Personal lab for repeatable security practice — Docker/WordPress, Linux hardening, CCNA networking, AWS controls, and SIEM-style monitoring.
importance: 5
category: infrastructure
---

**Type:** Self-directed continuous lab · **Goal:** reproducible environments I can explain in interviews  

### Recruiter snapshot

Not a single product — a **practice platform** where I combine networking, Linux ops, web security, cloud baselines, and defensive tooling before I claim a skill on my CV.

## Lab building blocks

| Area | What I run / practice |
| ---- | --------------------- |
| Hypervisor / containers | VMware, Docker |
| OS | Ubuntu, Kali |
| Web stack | Apache, WordPress (authorized testing only) |
| Network | CCNA scenarios — VLAN, inter-VLAN, STP, OSPF, NAT, ACL, DHCP, DNS |
| Cloud | AWS EC2, IAM, VPC, Security Groups, Elastic IP, baseline hardening |
| Defensive stack | Wazuh, Elastic concepts, Suricata/pfSense (also used in AI-APW) |

## How I use it

1. **Build** a small topology or service stack.  
2. **Break / test** with an explicit hypothesis (misconfig, weak SG, bad ACL, vulnerable plugin path).  
3. **Observe** with logs, packet capture, or SIEM views.  
4. **Fix & retest**, then write short notes (see [Journal]({{ '/blog/' | relative_url }})).

## Example tracks

- **Docker WordPress security lab** — service bring-up, log review, hardening checks, safe web-vuln reproduction.  
- **Linux admin daily** — SSH, permissions, systemd, firewall/iptables-nftables, process and package hygiene.  
- **CCNA networking** — segment design, routing, ACL/NAT behavior verified at the packet/service level.  
- **AWS practice** — least-privilege IAM, Security Groups, host hardening on EC2.  
- **Blue-team habits** — alert triage mindset, log paths, correlation ideas used later in AI-APW.

## Boundaries

All offensive testing stays in **owned or explicitly authorized** environments. No production scanning of third parties from this lab.

## Skills demonstrated

Lab design · documentation · Linux/network ops · cloud security basics · web-lab hygiene · defensive tooling familiarity
