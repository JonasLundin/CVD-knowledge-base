---
type: Role
title: 'Role: Vendor PSIRT'
description: Product Security Incident Response Team responsible for receiving, analyzing,
  and fixing vulnerabilities in vendor products.
category: role
tags:
- cvd
- role
- psirt
- first
- vendor
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: first-psirt-services-framework
  resource: https://www.first.org/standards/frameworks/psirt/
  title: FIRST PSIRT Services Framework v1.1
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2021-03-01T00:00:00Z'
- id: first-cvd-guide
  resource: https://www.first.org/global/sigs/vulnerability-coordination/multiparty/cvd-v1.1
  title: Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1)
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2020-09-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: FIRST PSIRT Services Framework
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Vendor PSIRT** (Product Security Incident Response Team) is the designated operational team within a software or hardware vendor responsible for managing the lifecycle of vulnerabilities impacting the vendor's products, services, and digital offerings.

# Core Capabilities under the FIRST Framework

Under the FIRST PSIRT Services Framework:
- **Intake & Receipt**: Maintaining `/.well-known/security.txt` and secure PGP intake inboxes.
- **Technical Triage**: Laboratory reproduction, CVSS severity scoring, and CWE weakness classification.
- **Remediation Management**: Partnering with core engineering squads to author, test, and backport security patches.
- **CVE Administration**: Operating as an authorized CVE Numbering Authority (CNA) to assign CVE IDs[^first-cvd-guide].
- **Advisory & VEX Issuance**: Generating machine-readable CSAF 2.0 advisories.

# Related concepts
- [Finder (Security Researcher)](finder.md)
- [CVE Numbering Authority (CNA)](cna.md)
- [Triage, Reproduction, and Impact Assessment](../process/triage-and-validation.md)
- [Advisory Publication and Patch Release](../process/advisory-publication.md)

[^first-psirt-services-framework]: Forum of Incident Response and Security Teams (FIRST), FIRST PSIRT Services Framework v1.1, https://www.first.org/standards/frameworks/psirt/
[^first-cvd-guide]: Forum of Incident Response and Security Teams (FIRST), Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1), https://www.first.org/global/sigs/vulnerability-coordination/multiparty/cvd-v1.1
