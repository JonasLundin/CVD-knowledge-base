---
type: Concept
title: CVE Root Hierarchy and Delegation Model
description: Governance structure connecting the Secretariat, Top-Level Roots, and
  Roots to individual CNAs across industry domains.
category: programme
tags:
- cvd
- programmes
- cve
- roots
- cnas
- hierarchy
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
  authority_level: binding
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CVE Program** employs a distributed hierarchical delegation model ensuring scalable governance, scoping, and oversight of hundreds of CVE Numbering Authorities (CNAs) worldwide[^cve-operational-rules-4-2-0].

# Governance Tiers

1. **CVE Secretariat**: Administered by MITRE Corporation under CVE Board oversight. The Secretariat manages primary registry services, user authentication, global namespace infrastructure, and backup CNA of Last Resort (CNA-LR) operations.
2. **Top-Level Roots (TL-Roots)**: Organizations delegated overarching regional or sectoral authority. Notably, **CISA** serves as a Top-Level Root for civilian US infrastructure, while **ENISA** operates as a Top-Level Root (TL-Root) covering European Member States, coordinating national CSIRTs and synchronizing data with the European Vulnerability Database (EUVD).
3. **Roots**: Entities managing designated families of operational CNAs within defined market sectors or ecosystems. For example, **Siemens Root** oversees industrial automation, OT, and medical technology CNAs; **Red Hat Root** coordinates open-source project CNAs; and **Google Root** administers products across the Google and Android ecosystem.
4. **CNAs**: Vendor, researcher, and coordinator organizations authorized to assign CVE IDs to vulnerabilities strictly within their approved scope definitions.

# Operational Contract and Scope Rules

Under Section 3 and Section 4 of the CNA Operational Rules, Roots actively supervise child CNAs, conduct regular operational reviews, resolve scope conflicts, and handle escalations if a child CNA fails to publish records within mandatory clocks.

# Related concepts
- [Roots and CNAs Index](index.md)
- [CNA Role](/roles/cna.md)
- [ENISA Root](enisa-root.md)

[^cve-operational-rules-4-2-0]: CVE Program, CVE Numbering Authority (CNA) Operational Rules, Version 4.2.0, https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.2.0.pdf
