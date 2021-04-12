---
aliases:
- 2bx-cyd-ejk
control: '3.14'
disable_edit: true
framework: cis-docker
kind: documentation
rule_category:
- Runtime Agent
scope: docker
security: compliance
source: docker
title: Docker server certificate key file permissions are set to 400
type: security_rules
---

## Description

You should verify that the Docker server certificate key file, the file that is passed along with the `--tlskey` parameter, has permissions of 400.

## Rationale

The Docker server certificate key file should be protected from any tampering or unneeded reads. It holds the private key for the Docker server certificate. It must therefore have permissions of 400 to ensure that the certificate key file is not modified.

## Audit

Verify that the Docker server certificate key file has permissions of `400` by running: 
```
stat -c %a <path to Docker server certificate key file>
```

## Remediation

You should execute the following command: `chmod 400 <path to Docker server certificate key file>`

This sets the Docker server certificate key file permissions to 400.

## Impact

None

## Default Value

By default, the permissions for the Docker server certificate key file might not be 400. The default file permissions are governed by the operating system or user specific umask values.

## References

1. https://docs.docker.com/registry/insecure/
2. https://docs.docker.com/engine/security/https/

## CIS Controls

Version 6

14.4 Protect Information With Access Control Lists All information stored on systems shall be protected with file system, network share, claims, application, or database specific access control lists. These controls will enforce the principle that only authorized individuals should have access to the information based on their need to access the information as a part of their responsibilities.

Version 7

14.6 Protect Information through Access Control Lists Protect all information stored on systems with file system, network share, claims, application, or database specific access control lists. These controls will enforce the principle that only authorized individuals should have access to the information based on their need to access the information as a part of their responsibilities.
