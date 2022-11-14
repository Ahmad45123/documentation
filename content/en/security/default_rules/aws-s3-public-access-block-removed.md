---
aliases:
- 4cd-f56-dfa
- /security_monitoring/default_rules/4cd-f56-dfa
- /security_monitoring/default_rules/aws-s3-public-access-block-removed
control: 7.2.1
disable_edit: true
framework: pci
iaas: aws
integration_id: s3
kind: documentation
rule_category:
- Cloud SIEM (Log Detection)
scope: s3
security: attack
source: cloudtrail
tactic: TA0005-defense-evasion
technique: T1562-impair-defenses
title: AWS S3 Public Access Block removed
type: security_rules
---

## Goal
Detect when the S3 Public Access Block configuration has been removed 

## Strategy
This rule lets you monitor this CloudTrail API call to detect if an attacker is deleting the S3 Public Access Block configuration:

* [DeleteAccountPublicAccessBlock][1]

## Triage and response
1. Determine who the user was who made this API call.
2. Contact the user and inform them of best practices of enabling Public Access Block on S3 buckets.
3. Re-enable Public Access Block on the S3 bucket.

More details on S3 Public Block Public Access can be found [here][2].

[1]: https://docs.aws.amazon.com/cli/latest/reference/s3api/delete-public-access-block.html
[2]: https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-block-public-access.html

## Changelog
18 March 2022 - updated severity and query.
