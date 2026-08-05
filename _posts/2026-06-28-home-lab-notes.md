---
layout: post
title: "Home lab notes: Linux, Docker, and cloud practice"
date: 2026-06-28 18:45:00+0700
description: How I structure a personal security lab so skills stay explainable in interviews.
tags: [home-lab, linux, docker, cloud, aws, documentation]
categories: [infrastructure]
---

Recruiters often ask *“what have you actually run?”* My answer is this lab: a small set of environments I rebuild on purpose so I can explain failures, not only happy paths.

## What runs here

- **Linux VMs** (Ubuntu) for services, permissions, systemd, and firewall practice  
- **Docker** stacks (e.g. WordPress + Apache) for repeatable web and ops drills  
- **AWS EC2** for IAM, Security Groups, and baseline host hardening  
- **Defensive tooling** where it fits the scenario (log paths, Wazuh concepts; full SIEM topology lives mainly in the [AI-APW]({{ '/projects/10_ai_apw/' | relative_url }}) write-up)

## Working rules

1. **One hypothesis per session** — e.g. “this Security Group is too open,” “this ACL blocks return traffic,” “this plugin path lacks a capability check.”  
2. **Observe with a tool** — logs, `tcpdump`/Wireshark, or SIEM views — not guesswork.  
3. **Write the delta** — what broke, what fixed it, what I’d check in a real environment.  
4. **Stay authorized** — only systems I own or am allowed to test.

## Why this matters for a junior hire

The lab is not a trophy list. It is how I keep **Linux + network + web + cloud** connected so I can join a team without treating each topic as a separate course chapter.

Related: [Security Home Lab project]({{ '/projects/05_security_home_lab/' | relative_url }}) · [Roadmap]({{ '/roadmap/' | relative_url }})
