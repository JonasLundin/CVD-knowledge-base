---
type: Role
title: CVE Numbering Authority (CNA) Types
description: Categorization of CNAs by organizational scope and operational function within the CVE Program.
category: role
tags:
- cve
- cna
- cna-types
status: draft
generated:
  by: manual-curation
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
  authority_level: operational
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The CVE Program recognizes distinct classes of **CVE Numbering Authorities (CNAs)** tailored to different operational contexts[^cve-operational-rules-4-2-0].

# Primary CNA Categories
1. **Vendor / Developer CNA**: Assigns IDs exclusively for vulnerabilities discovered in its own proprietary or distributed software products.
2. **Open-Source Project CNA**: Assigns IDs for software maintained by a specific open-source community or foundation (e.g., Apache, Linux Kernel, Python).
3. **National / Regional CSIRT CNA**: Assigns IDs for vulnerabilities reported within its national jurisdiction or geographic sphere of authority.
4. **Coordinator / Researcher CNA**: Assigns IDs for vulnerabilities reported through third-party bug bounty platforms or independent security research firms.

# Related concepts
- [CNA of Last Resort (CNA-LR)](cna-lr.md)
- [CNA Operational Rules](../cna-operational-rules/index.md)

[^cve-operational-rules-4-2-0]: CVE Program, CVE Numbering Authority (CNA) Operational Rules, Version 4.2.0, https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.2.0.pdf
