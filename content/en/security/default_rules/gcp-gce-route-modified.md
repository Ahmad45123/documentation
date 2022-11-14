---
aliases:
- 3b3-32c-73c
- /security_monitoring/default_rules/3b3-32c-73c
- /security_monitoring/default_rules/gcp-gce-route-modified
disable_edit: true
integration_id: gcp.gce.route
kind: documentation
rule_category:
- Cloud SIEM (Log Detection)
scope: gcp.gce.route
security: compliance
source: gcp
title: GCP GCE network route created or modified
type: security_rules
---

## Goal
Detect when a firewall rule is created or modified. 

## Strategy
This rule lets you monitor GCP GCE activity audit logs to determine if a firewall is being adjusted by showing you when any of the following methods are invoked:

* `beta.compute.routes.insert`
* `beta.compute.routes.patch`

## Triage and response
1. Veirify that the GCP route is configured properly and that the user intended to modify the firewall.
