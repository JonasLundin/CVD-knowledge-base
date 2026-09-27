---
type: Role
title: CNA of Last Resort (CNA-LR)
description: Designated authority responsible for assigning CVE IDs to vulnerabilities not covered by any scoped CNA.
category: role
tags:
- cve
- cna
- cna-lr
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

A **CNA of Last Resort (CNA-LR)** is an authorized entity that assigns CVE IDs to vulnerabilities affecting products that do not fall within the scope of any existing operational CNA (§4.2.4)[^cve-operational-rules-4-2-0].

# Operational Role
- **Universal Safety Net**: Prevents valid vulnerabilities in orphaned or small vendor products from going uncataloged.
- **Root Operations**: Each Root acts as the CNA-LR for its designated domain.
- **Verification**: Conducts independent verification of public disclosure and vulnerability validity prior to assignment.

# Related concepts
- [CNA Types](cna-types.md)
- [Section 4: CNA Operational Rules](../cna-operational-rules/section-4-cna-operational-rules.md)

[^cve-operational-rules-4-2-0]: CVE Program, CVE Numbering Authority (CNA) Operational Rules, Version 4.2.0, https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.2.0.pdf
