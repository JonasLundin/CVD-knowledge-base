---
type: Role
title: 'Role: Coordinator'
description: Neutral intermediary (e.g., CERT/CC, national CSIRT) assisting finders
  and vendors during complex or unresponsive disclosures.
category: role
tags:
- cvd
- role
- coordinator
- csirt
- cert-cc
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: iso-iec-29147
  resource: https://www.iso.org/standard/72311.html
  title: "ISO/IEC 29147:2018 Information technology \u2014 Security techniques \u2014\
    \ Vulnerability disclosure"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2018-10-01T00:00:00Z'
- id: nis2-directive
  resource: http://data.europa.eu/eli/dir/2022/2555/oj
  title: Directive (EU) 2022/2555 on measures for a high common level of cybersecurity
    across the Union (NIS2)
  author: European Parliament and Council of the European Union
  last_modified: '2022-12-14T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: ISO/IEC 29147 Clause 4.3, NIS2 Article 12
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Coordinator** is a trusted, neutral third-party organization (such as CERT/CC, a national CSIRT designated under NIS2 Article 12, or an open-source security committee) that facilitates communication and remediation between finders and vendors[^iso-iec-29147][^nis2-directive].

# Coordinator Triggers & Mandates

Coordinators intervene in vulnerability disclosure workflows under specific conditions:
1. **Unresponsive Vendors**: The finder cannot reach the vendor or receives no response after repeated inquiries.
2. **Multi-Party Vulnerabilities**: The vulnerability impacts multiple competing vendors or an international standard.
3. **Disputed Vulnerabilities**: The vendor and finder disagree on exploitability, impact, or disclosure timeline.
4. **National Security & Critical Infrastructure**: The flaw impacts critical national infrastructure or Union essential entities.

# Related concepts
- [Finder (Security Researcher)](finder.md)
- [Vendor PSIRT](vendor-psirt.md)
- [Multi-Party Vulnerability Coordination](../process/multi-party-coordination.md)
- [NIS2 Article 11: Coordinated Vulnerability Disclosure](../law/nis2-article-11.md)

[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
[^nis2-directive]: European Parliament and Council of the European Union, Directive (EU) 2022/2555 on measures for a high common level of cybersecurity across the Union (NIS2), http://data.europa.eu/eli/dir/2022/2555/oj
