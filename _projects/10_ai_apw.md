---
layout: page
title: AI-Powered Alert Prioritization for Wazuh
description: Capstone project that turns Wazuh and Suricata telemetry into prioritized, correlated SOC alerts with LLM-assisted triage and Telegram notifications.
img: assets/img/projects/ai-apw-architecture.png
importance: 1
category: cybersecurity
---

**AI-APW** is a team capstone project at the International School, Duy Tan University. It adds an intelligent triage layer to a Wazuh deployment so SOC analysts can investigate the most relevant alerts first instead of treating every event as equally urgent.

My contributions span **backend development, AI-pipeline development, and DevOps/system integration**. I worked on the services that collect and normalize alerts, connect the lab components, apply triage logic, and deliver actionable notifications.

## Problem and approach

High volumes of security alerts create noise and slow down investigation. AI-APW keeps the Wazuh detection layer in place, then enriches its alerts with normalized context, correlation, scoring, and a human-readable notification.

The pipeline does not silently discard events. Potential false positives are labelled for analyst review, while critical rules, high-confidence threats, and correlated attack campaigns can override a low model score and still notify the SOC.

## Lab architecture

The controlled lab separated the web workload from the security and monitoring services. Traffic passed through pfSense with Suricata, while Wazuh collected both network and host/application telemetry before the AI-APW pipeline processed it.

![AI-APW lab topology: attacker, pfSense, web server, Wazuh, and AI/SOC services]({{ '/assets/img/projects/ai-apw-architecture.png' | relative_url }})

_Figure: project lab topology and data flow, recreated from the capstone implementation evidence._

| Layer                | Components and responsibility                                                                 |
| -------------------- | --------------------------------------------------------------------------------------------- |
| Attack simulation    | Kali Linux generated authorized test traffic against DVWA.                                    |
| Network boundary     | pfSense forwarded lab traffic and Suricata produced network IDS alerts.                       |
| Application workload | Ubuntu 22.04 hosted DVWA and a Wazuh agent to expose host and web-access signals.             |
| SIEM                 | Wazuh Manager and Indexer ingested, analyzed, and indexed alerts in `wazuh-alerts-*`.         |
| Triage and response  | A Python pipeline normalized, correlated, scored, and routed prioritized results to Telegram. |

## Alert-triage pipeline

1. **Collect:** Query new alerts from the Wazuh Indexer over HTTPS, using dynamic lookback and agent-aware polling to reduce missed events and uneven load.
2. **Filter and normalize:** Include configured custom rules and always re-evaluate higher-level events. Raw alerts are mapped to a common structure containing timestamp, agent, rule, network, HTTP, Suricata, and identity fields.
3. **Enrich and correlate:** Normalize attack types, group related events by source, destination, and attack type, then identify possible multi-stage campaigns.
4. **Score:** Combine a deterministic heuristic score with LLM-assisted analysis. The heuristic accounts for Wazuh rule level, attack type, correlation size, and indicators such as security-tool user agents.
5. **Notify:** Apply critical-rule and campaign overrides, then deliver an evidence-rich Telegram alert with IOCs, context, correlation information, and recommended SOC actions.

## Technology and implementation details

- **Detection and telemetry:** Wazuh 4.x, Wazuh agents, pfSense 2.7.2, Suricata, and EVE JSON logs.
- **Pipeline:** Python service launched through `bin/run_pipeline.py`, with modular collector, normalization, correlation, heuristic scoring, LLM triage, and notification components.
- **Configuration:** environment-based settings for Wazuh API/Indexer endpoints, polling interval, rule filters, correlation/deduplication windows, and notification credentials. Secrets are supplied at deployment time rather than stored in source control.
- **Operational guardrails:** HTTPS integration with Wazuh, agent-balanced queries, alert-audit logging, false-positive labelling rather than deletion, and a plain-text fallback if Telegram Markdown formatting fails.

## Deployment workflow

1. Provision the isolated lab components: pfSense/Suricata, an Ubuntu web server with DVWA, Wazuh, and an AI-APW host.
2. Install and connect Wazuh agents on the firewall and web server; verify that firewall, IDS, system, and web-access logs are searchable in `wazuh-alerts-*`.
3. Configure Suricata logging and lab-only signatures, then verify that telemetry crosses the firewall, SIEM, and indexer as expected.
4. Provide the pipeline configuration and secrets through environment variables; configure filtering levels, correlation windows, Wazuh access, LLM access, and Telegram delivery.
5. Start the pipeline, validate its startup logs and connectivity, then run controlled attack simulations to verify detection, prioritization, and notification.

## Demonstration evidence

The following screenshots are taken from the project test documentation. They show the same test chain from alert discovery through operational notification.

![Wazuh Threat Hunting view with Suricata-derived alerts indexed for the pfSense agent]({{ '/assets/img/projects/ai-apw-wazuh-threat-hunting.png' | relative_url }})

_Wazuh Threat Hunting confirms that Suricata-derived alerts are indexed and queryable for investigation._

![AI-APW pipeline logs showing processing, triage completion, and Telegram delivery]({{ '/assets/img/projects/ai-apw-pipeline-logs.png' | relative_url }})

_Pipeline logs show alert processing, triage completion, and notification handling._

![Telegram notification showing a high-priority SQL injection alert with evidence]({{ '/assets/img/projects/ai-apw-telegram-alert.png' | relative_url }})

_The SOC notification carries severity, evidence, context, and recommended follow-up actions._

## Validation results

The end-to-end validation used an authorized SQL injection campaign with `sqlmap` against DVWA in the lab. Suricata detected the network behavior, Wazuh indexed both network and host-side signals, and AI-APW normalized, scored, correlated, and notified on the event.

| Metric in the documented lab test | Result                                                      |
| --------------------------------- | ----------------------------------------------------------- |
| Alert detection rate              | 100% for the test scenarios                                 |
| Estimated false-positive rate     | Approximately 12%                                           |
| Detection-to-notification latency | 3-7 seconds on average; approximately 10 seconds worst case |
| Telegram delivery rate            | 100% during the test window                                 |

These are **controlled-lab results**, not production benchmarks. The documentation also records practical improvements for future iterations: enforce a rule-level severity baseline when LLM labels are inconsistent, improve web-log decoder mapping so client IP context is preserved, and continue validating notification formatting.

## What this project demonstrates

- Building and integrating a multi-layer SOC lab across firewall, IDS, web server, SIEM, and AI-assisted automation.
- Translating raw security telemetry into structured, explainable analyst context.
- Applying safe alert-triage guardrails so high-impact attacks are not hidden by model or filter decisions.
- Testing an end-to-end detection workflow with reproducible evidence rather than relying on a dashboard-only demo.
