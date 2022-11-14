---
aliases:
- 74f-6b9-4a3
- /security_monitoring/default_rules/74f-6b9-4a3
- /security_monitoring/default_rules/unrestricted_icmp_access
disable_edit: true
integration_id: ec2
kind: documentation
rule_category:
- Posture Management (Cloud)
- Cloud Security Management
source: ec2
title: Inbound ICMP access is restricted
type: security_rules
---

## Description

Reduce the probability of a breach by checking [EC2 security groups][1] for inbound rules that allow unfettered access to host using the Internet Control Message Protocol (ICMP), a protocol commonly used to troubleshoot TCP/IP networks and deliver IP packets, and restrict access.

## Rationale

Malicious activity, such as denial-of-service (DoS) attacks and Smurf/Fraggle attacks, can occur when permitting unfettered access to this port.

## Remediation

### From the console

Follow the [Security group rules][2] docs to learn how to restrict access to host using the ICMP.

### From the command line

1. Run `describe-security-groups` with a filter to [expose security groups][1] that allow access to host using ICMP.

    {{< code-block lang="bash" filename="describe-security-group.sh" >}}
    aws ec2 describe-security-groups
	    --filters Name=ip-permission.protocol,Values=icmp Name=ip-permission.cidr,Values='192.0.2.0/24'
	    --query 'SecurityGroups[*].{Name:GroupName}'
    {{< /code-block >}}

[1]: https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html
[2]: https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html#SecurityGroupRules
