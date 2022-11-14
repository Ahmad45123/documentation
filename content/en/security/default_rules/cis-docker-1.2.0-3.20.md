---
aliases:
- pv5-2tt-sp9
- /security_monitoring/default_rules/pv5-2tt-sp9
- /security_monitoring/default_rules/cis-docker-1.2.0-3.20
control: '3.20'
disable_edit: true
framework: cis-docker
integration_id: docker
kind: documentation
rule_category:
- Posture Management (Infra)
- Cloud Security Management
scope: docker
security: compliance
source: docker
title: Default Docker configuration file is owned by the root account and group -
  RHEL
type: security_rules
---

## Description

You should verify that the `/etc/sysconfig/docker` file individual ownership and group ownership is correctly set to root.

## Rationale

The `/etc/sysconfig/docker` file contains sensitive parameters that may alter the behavior of the Docker daemon. It should therefore be individually owned and group owned by root to ensure that it is not modified by less privileged users.

## Audit

Verify that the `/etc/sysconfig/docker` file is individually owned and group-owned by root by running: 
```
stat -c %U:%G /etc/sysconfig/docker | grep -v root:root
```
The command should return no results.

## Remediation

Run the following command: `chown root:root /etc/sysconfig/docker`

This sets the ownership and group ownership for the file to root.

## Impact

None

## Default value

This file may not be present on the system, and in this case, this recommendation is not applicable.

## References

1. https://docs.docker.com/engine/admin/configuring/

## CIS controls

Version 6

5.1 Minimize And Sparingly Use Administrative Privileges Minimize administrative privileges and only use administrative accounts when they are required. Implement focused auditing on the use of administrative privileged functions and monitor for anomalous behavior.
