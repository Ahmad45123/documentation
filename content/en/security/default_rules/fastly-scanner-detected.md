---
aliases:
- 216-b0c-f83
- /security_monitoring/default_rules/216-b0c-f83
- /security_monitoring/default_rules/fastly-scanner-detected
disable_edit: true
integration_id: fastly
kind: documentation
rule_category:
- Cloud SIEM (Log Detection)
scope: fastly
security: attack
source: fastly
tactic: TA0001-initial-access
technique: T1190-exploit-public-facing-application
title: Fastly HTTP Requests from Security Scanner
type: security_rules
---

## Goal
Detect when a web application is being scanned. This identifies attacker IP addresses who are not trying to hide their attempt to attack your system. More advanced hackers will use an inconspicuous user agent. 

## Strategy
Inspect the user agent in the HTTP headers to determine if an IP is scanning your application and generate an `INFO` signal. 

## Triage and response
1. Determine if this IP is making authenticated requests to the application.
2. If the IP is making authenticated requests to the application:
 * Investigate the HTTP logs and determine if the user is attacking your application.

The HTTP headers in the query are from [darkqusar][1]'s [gist][2]. 

[1]: https://gist.github.com/darkquasar
[2]: https://gist.github.com/darkquasar/84fb2cec6cc1668795bd97c02302d380
