---
aliases:
- sme-jsx-2n6
- /security_monitoring/default_rules/sme-jsx-2n6
- /security_monitoring/default_rules/cis-kubernetes-1.5.1-1.2.7
control: 1.2.7
disable_edit: true
framework: cis-kubernetes
integration_id: kubernetes
kind: documentation
rule_category:
- Posture Management (Infra)
- Cloud Security Management
scope: kubernetes
security: compliance
source: kubernetes
title: API server only allows explicitly authorized requests
type: security_rules
---

## Description

Do not always authorize all requests.

## Rationale

The API Server, can be configured to allow all requests. This mode should not be used on any production cluster.

## Audit

Run the following command on the master node:
```
ps -ef | grep kube-apiserver
```
Verify that the `--authorization-mode` argument exists and is not set to `AlwaysAllow`.

## Remediation

Edit the API server pod specification file `/etc/kubernetes/manifests/kube-apiserver.yaml` on the master node and set the `--authorization-mode` parameter to values other than `AlwaysAllow`. One such example could be as below:

```
--authorization-mode=RBAC
```

## Impact

Only authorized requests will be served.

## Default value

By default, `AlwaysAllow` is not enabled.

## References

1. [https://kubernetes.io/docs/admin/kube-apiserver/ ][1]
2. [https://kubernetes.io/docs/admin/authorization/node/ ][2]


## CIS controls

Version 6.9.1 Limit Open Ports, Protocols, and Services - Ensure that only ports, protocols, and services with validated business needs are running on each system. 

Version 7.9.2 Ensure Only Approved Ports, Protocols and Services Are Running - Ensure that only network ports, protocols, and services listening on a system with validated business needs, are running on each system.              

[1]: https://kubernetes.io/docs/admin/kube-apiserver/ 
[2]: https://kubernetes.io/docs/admin/authorization/node/
