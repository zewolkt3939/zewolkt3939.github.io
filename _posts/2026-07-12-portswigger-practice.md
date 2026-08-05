---
layout: post
title: How I use PortSwigger labs for web security practice
date: 2026-07-12 22:15:00+0700
description: A repeatable AppSec practice loop — impact, evidence, root cause, fix, retest — with Burp Suite.
tags: [web-security, portswigger, burp-suite, appsec]
categories: [security]
---

PortSwigger Web Security Academy is useful only if the output looks like **assessment notes**, not a checklist of finished walkthroughs. This is the loop I use.

## Practice loop

1. **Impact first** — what can an attacker actually do (read data, escalate, pivot)?  
2. **Reproduce** — in the Academy lab or my own authorized Docker/WordPress lab.  
3. **Evidence** — capture the HTTP request/response chain in Burp (and code paths when available).  
4. **Root cause** — missing authZ, trust of client input, unsafe deserialization, etc.  
5. **Mitigation note** — something a developer could implement (validation, capability checks, CSRF tokens, least privilege).  
6. **Retest** — confirm the lesson stuck.

## Topics I rotate through

SQL injection · XSS · CSRF · XXE · SSRF · authentication · access control · business logic · sessions · OAuth · JWT

## Link to real work

A year of [WordPress plugin security research at Fore-Z]({{ '/projects/04_wordpress_security_research/' | relative_url }}) made this loop mandatory: scanners without root-cause notes waste engineering time. Labs train the same reporting muscle.

Full track page: [Web Application Security Practice]({{ '/projects/06_web_security_track/' | relative_url }})
