---
aliases:
- w6m-rmy-hra
- /security_monitoring/default_rules/w6m-rmy-hra
- /security_monitoring/default_rules/azure_login_explicitly_denied_mfa
disable_edit: true
integration_id: azure
kind: documentation
rule_category:
- Cloud SIEM (Log Detection)
security: attack
source: azure
tactic: TA0006-credential-access
technique: T1110-brute-force
title: Azure Login Explicitly Denied MFA
type: security_rules
---

## Goal
Detect and identify the network IP address when multiple user accounts failed to complete the MFA process.

## Strategy
Monitor Azure Active Directory Sign-in logs and detect when any `@evt.category` is equal to `SignInLogs`, `@properties.authenticationRequirement` is equal to `multiFactorAuthentication` and `@evt.outcome` is equal to `failure`.

## Triage and response 
1. Inspect the log and determine if this was a valid login attempt.
2. If the user was compromised, rotate user credentials.
