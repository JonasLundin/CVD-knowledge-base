---
type: Role
title: 'Role: CVE Numbering Authority (CNA)'
description: Organization authorized by the CVE Program to assign CVE IDs to vulnerabilities
  within their designated scope.
category: role
tags:
- cvd
- role
- cna
- cve
- mitre
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: cve-operational-rules-4-2-0
  resource: https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.2.0.pdf
  title: CVE Numbering Authority (CNA) Operational Rules, Version 4.2.0
  author: CVE Program
  last_modified: '2026-08-25T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: CVE CNA Operational Rules
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **CVE Numbering Authority (CNA)** is an organization authorized by the CVE Program to assign CVE Identifiers to vulnerabilities affecting products within their agreed-upon organizational scope and to populate and publish official CVE Records[^cve-operational-rules-4-2-0].

# CNA Types & Scopes

- **Vendor / Project CNAs**: Assign CVE IDs strictly for vulnerabilities in their own commercial products or open-source projects (e.g. Red Hat, Microsoft, Apache, Linux Foundation).
- **Coordinator CNAs**: Assign CVE IDs for vulnerabilities reported to them involving third-party products (e.g. CERT/CC, JPCERT/CC).
- **National / Regional CNAs**: Assign CVE IDs for products developed within a specific geographic territory.
- **Root CNAs**: Supervise and onboard child CNAs within a specific technology domain or geopolitical region.

# Related concepts
- [The CVE Program](../programmes/cve-program.md)
- [Section 1: CNA Program Overview](../programmes/cve/cna-operational-rules/section-1-introduction.md)
- [Section 3: CVE ID Assignment Rules](../programmes/cve/cna-operational-rules/section-4-cna-operational-rules.md)
- [cnaContainer (CNA Content)](../programmes/cve/record-format/cna-container.md)

[^cve-operational-rules-4-2-0]: CVE Program, CVE Numbering Authority (CNA) Operational Rules, Version 4.2.0, https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.2.0.pdf
