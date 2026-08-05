---
layout: page
title: Web Application Security Practice Track
description: Structured PortSwigger / OWASP-oriented practice — reproduce, root-cause, mitigate, retest — with Burp Suite and clear notes.
importance: 6
category: cybersecurity
---

**Focus:** Application security fundamentals for junior security / AppSec-adjacent roles  
**Tools:** Burp Suite · browser devtools · notes in the [Journal]({{ '/blog/' | relative_url }})  
**Background:** Builds on a year of WordPress plugin research at Fore-Z

### Recruiter snapshot

I treat web labs like mini engagements: **impact → evidence → root cause → fix → retest**, not a scoreboard of unfinished walkthroughs.

## Workflow

1. Understand the vulnerable behavior and business impact.  
2. Reproduce safely in an authorized training environment (PortSwigger Academy, personal lab).  
3. Confirm the mechanism in HTTP requests/responses (and code when available).  
4. Write mitigation / prevention notes a developer could act on.  
5. Retest to lock in the lesson.

## Topic coverage (in progress / rotating)

SQL injection · XSS · CSRF · XXE · SSRF · authentication flaws · access control · business logic · session management · OAuth · JWT

## How this connects to real work

| Lab habit | Real-world analogue |
| --------- | ------------------- |
| Read the request chain | Burp history / proxy in assessments |
| Capability & authZ checks | Access-control bugs in apps and plugins |
| Clear write-ups | Ticket / VA report quality |
| Retest after fix | Verification in remediations |

## Related writing

- [How I use PortSwigger labs]({{ '/blog/2026/how-i-use-portswigger-labs-for-web-security-practice/' | relative_url }})  
- Internship: [WordPress Plugin Security Research]({{ '/projects/04_wordpress_security_research/' | relative_url }})
