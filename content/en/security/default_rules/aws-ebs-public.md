---
aliases:
- g1t-jj4-k8k
- /security_monitoring/default_rules/g1t-jj4-k8k
- /security_monitoring/default_rules/aws-ebs-public
disable_edit: true
integration_id: ebs
kind: documentation
rule_category:
- Posture Management (Cloud)
- Cloud Security Management
source: ebs
title: EBS volume snapshot is not publicly shared with other AWS accounts
type: security_rules
---

## Description

Secure Amazon Elastic Block Store (EBS) snapshots.

## Rationale

Publicly shared Amazon EBS volume snapshots contain sensitive application data that can be seen, copied, and exploited.

## Remediation

### From the console

Follow the [EBS encryption][1] docs to learn how to implement EBS encryption. Public snapshots, which are encrypted by default, are not supported

    **Note**: You can share an encrypted snapshot with specific accounts.

### From the command line

1. Run `enable-ebs-encryption-by-default` to [enable encryption for your account in the current region][2].

2. Run `get-ebs-encryption-by-default` to confirm encryption is enabled.

See the [Set encryption defaults using the API and CLI][3] docs for additional commands related to EBS encryption.

[1]: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html#how-ebs-encryption-works
[2]: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html#encryption-by-default-api
[3]: https://awscli.amazonaws.com/v2/documentation/api/latest/reference/ec2/enable-ebs-encryption-by-default.html
