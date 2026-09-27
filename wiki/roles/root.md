---
type: Role
title: CVE Root
description: Supervisory authority within the CVE Program overseeing subordinate CNAs within a specific geographic or technical domain.
category: role
tags:
- role
- cve
- root
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
  authority_level: contractual
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Root** within the CVE Program is an organization authorized by the CVE Board and Secretariat to manage a specific family of CVE Numbering Authorities (CNAs) within a designated domain or sector[^cve-operational-rules-4-2-0].

# Governance and Supervisory Functions

Roots are responsible for recruiting, onboarding, and training candidate CNAs within their technical or industrial purview. They continuously monitor child CNA performance, verify adherence to mandatory publication clocks, resolve inter-CNA scope conflicts, and operate as a CNA of Last Resort (CNA-LR) for vulnerabilities within their domain when no child CNA is scoped. Prominent Roots include Siemens Root (industrial automation) and Red Hat Root (open-source software).

# Related concepts
- [Roles Index](index.md)
- [Top-Level Root](top-level-root.md)
- [CNA Role](cna.md)

[^cve-operational-rules-4-2-0]: CVE Program, CVE Numbering Authority (CNA) Operational Rules, Version 4.2.0, https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.2.0.pdf
