---
layout: page
title: AI-Powered Alert Prioritization for Wazuh (AI-APW)
description: Capstone SOC pipeline — Wazuh + Suricata telemetry → correlation, scoring, LLM-assisted triage, and Telegram alerts for analysts.
img: assets/img/projects/ai-apw-architecture.png
importance: 1
category: cybersecurity
---

**Role:** Backend, AI-pipeline, and DevOps/system integration · **Team capstone** · Duy Tan University (International School) · Aug–Dec 2025  
**Repo:** [github.com/zewolkt3939/-AI-Powered-Alert-Prioritization-for-Wazuh-](https://github.com/zewolkt3939/-AI-Powered-Alert-Prioritization-for-Wazuh-)

### Recruiter snapshot

| | |
|---|---|
| **Problem** | SOC alert volume hides high-impact attacks; analysts cannot treat every event equally. |
| **Solution** | Keep Wazuh as the detection layer; add a Python triage pipeline that normalizes, correlates, scores, and notifies. |
| **My work** | FastAPI-style collection services, normalization, correlation, heuristic + LLM scoring, Telegram delivery, lab integration. |
| **Lab result** | 100% detection on test scenarios · ~3–7s average detect→notify · 100% Telegram delivery in the test window (controlled lab, not production SLA). |

---

**AI-APW** adds an intelligent triage layer on top of Wazuh so analysts investigate the most relevant alerts first. The pipeline **does not silently drop events**: likely false positives are labelled for review, while critical rules, high-confidence threats, and correlated campaigns can override a low model score and still notify the SOC.

## Lab architecture

Traffic crosses pfSense with Suricata; Wazuh collects network and host/application telemetry; AI-APW processes indexed alerts and notifies the team.

![AI-APW lab topology]({{ '/assets/img/projects/ai-apw-architecture.png' | relative_url }})

| Layer | Components |
| ----- | ---------- |
| Attack simulation | Kali → authorized tests against DVWA |
| Network boundary | pfSense + Suricata (IDS alerts) |
| Workload | Ubuntu 22.04, DVWA, Wazuh agent |
| SIEM | Wazuh Manager/Indexer (`wazuh-alerts-*`) |
| Triage & response | Python pipeline → Telegram |

## Pipeline (what I implemented and integrated)

1. **Collect** — Poll Wazuh Indexer over HTTPS (dynamic lookback, agent-aware queries).
2. **Normalize** — Map raw alerts to a common schema (timestamp, agent, rule, network, HTTP, Suricata, identity).
3. **Correlate** — Group by source/destination/attack type; flag multi-stage campaigns.
4. **Score** — Heuristic (rule level, attack type, correlation size, indicators) + LLM-assisted analysis.
5. **Notify** — Critical/campaign overrides; evidence-rich Telegram message (IOCs, context, suggested actions).

**Stack:** Wazuh 4.x · Suricata · pfSense · Python · env-based config (secrets not in git) · Telegram · modular `bin/run_pipeline.py` services.

## Evidence from the documented lab test

![Wazuh Threat Hunting]({{ '/assets/img/projects/ai-apw-wazuh-threat-hunting.png' | relative_url }})

_Suricata-derived alerts indexed and queryable in Wazuh._

![Pipeline logs]({{ '/assets/img/projects/ai-apw-pipeline-logs.png' | relative_url }})

_Processing, triage completion, notification handling._

![Telegram high-priority SQLi alert]({{ '/assets/img/projects/ai-apw-telegram-alert.png' | relative_url }})

_Severity, evidence, and recommended follow-up for the SOC._

## Validation (authorized SQLi campaign with sqlmap vs DVWA)

| Metric (lab) | Result |
| ------------ | ------ |
| Detection rate (test scenarios) | 100% |
| Est. false-positive rate | ~12% |
| Detect → notify latency | 3–7s avg · ~10s worst case |
| Telegram delivery | 100% in test window |

**Honest limits:** controlled-lab metrics only. Follow-ups: rule-level baseline when LLM labels disagree; improve web-log decoder mapping for client IP; harden notification formatting.

## What this shows a hiring manager

- End-to-end SOC lab integration (firewall → IDS → host → SIEM → automation)
- Explainable triage, not a black-box “AI magic” demo
- Operational guardrails (audit logging, FP labelling, secret handling)
- Ability to test and document a full detection workflow with reproducible evidence
