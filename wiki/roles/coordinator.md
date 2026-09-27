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
- id: first-cvd-guide
  resource: https://www.first.org/global/sigs/vulnerability-coordination/multiparty/guidelines-v1.1
  title: Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1)
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2020-09-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: ISO/IEC 29147 Clause 4.3, NIS2 Article 12
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Coordinator** is a trusted, neutral third-party organization (such as CERT/CC, a national CSIRT designated under NIS2 Article 12, or an open-source security committee) that facilitates communication and remediation between finders and vendors[^first-cvd-guide].

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
- [NIS2 Article 11: Coordinated Vulnerability Disclosure](../law/eu/nis2-article-12.md)

[^first-cvd-guide]: Forum of Incident Response and Security Teams (FIRST), Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1), https://www.first.org/global/sigs/vulnerability-coordination/multiparty/guidelines-v1.1
