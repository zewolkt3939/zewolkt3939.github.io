---
layout: page
title: WordPress Plugin Security Research (Fore-Z)
description: Internship research — source review of WordPress plugins, manual vulnerability assessment, and remediation documentation.
importance: 4
category: cybersecurity
---

**Role:** Cybersecurity Research Intern  
**Org:** Fore-Z  
**Period:** September 2024 – September 2025  
**Stack:** WordPress · PHP · Burp Suite

### Recruiter snapshot

Year-long research internship focused on **application security for WordPress ecosystems**: reading real plugin code, validating issues manually, and writing remediation-oriented reports.

## Responsibilities

- Reviewed **WordPress plugin source code** to identify security weaknesses (authz, input handling, unsafe APIs, common WP footguns).
- Performed **manual vulnerability assessment** with browser + Burp Suite in authorized scopes.
- Produced **remediation reports** that separate impact, evidence, and fix guidance — not just “scanner output.”

## Working method

1. Map plugin attack surface (admin vs public endpoints, AJAX, REST, capability checks).  
2. Trace data flow in PHP (sanitize/escape, nonces, capability checks, SQL/file operations).  
3. Confirm exploitability manually; avoid unvalidated scanner noise.  
4. Document root cause and practical fixes developers can apply.

## Skills demonstrated

Secure code review · web app testing · Burp Suite · PHP/WordPress security model · professional vulnerability reporting

## Continuity on this site

Structured web practice continues in the [Web Application Security Practice Track]({{ '/projects/06_web_security_track/' | relative_url }}) and journal notes on PortSwigger labs.
