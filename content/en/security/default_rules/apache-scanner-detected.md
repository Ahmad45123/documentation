---
aliases:
- 13a-810-14c
- /security_monitoring/default_rules/13a-810-14c
- /security_monitoring/default_rules/apache-scanner-detected
disable_edit: true
integration_id: apache
kind: documentation
rule_category:
- Cloud SIEM (Log Detection)
scope: apache
security: attack
source: apache
tactic: TA0001-initial-access
technique: T1190-exploit-public-facing-application
title: Apache HTTP requests from security scanner
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

The HTTP headers in the query are from [darkqusar][1]'s [gist][2] 

[1]: https://gist.github.com/darkquasar
[2]: https://gist.github.com/darkquasar/84fb2cec6cc1668795bd97c02302d380
