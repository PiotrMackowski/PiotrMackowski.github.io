---
permalink: /projects/
title: "Projects"
author_profile: false 
---

## ClosedSSPM
SaaS Security is often overlooked, understaffed and expensive. Even if you review the initial implementation, there's no way to keep on top of all the changes continuously. 3rd party point-in-time assessments are not fit for this by design. Your procurement pipeline of new SaaS does not account for the additional cost of SSPM tooling. I'd argue that securing the budget for enterprise licenses, which come with enterprise-grade controls, is already a win at most places.

[ClosedSSPM](https://closedsspm.com/) solves this problem for ServiceNow, Snowflake, and other platforms. It audits platforms for security misconfigurations and reports findings in HTML, JSON, CSV, or SARIF. The pluggable connector architecture allows adding new platforms without touching core code. Custom policies can be defined in YAML.

## Zoom auto-joiner 
[Auto-joiner](https://github.com/PiotrMackowski/auto-joiner) lets you automatically join your Zoom meetings. Packaged as a menu bar app for convenience. In essence, it polls your local macOS calendar and triggers the Zoom desktop app at the right time. To leverage this, first synchronize your calendar(s) by adding them in System Settings > Internet Accounts.