---
type: Role
title: 'Role: Authorized Data Publisher (ADP)'
description: Designated entity authorized to enrich published CVE records with supplementary
  scores and metadata.
category: role
tags:
- cvd
- role
- adp
- cisa
- enrichment
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: cve-program
  resource: https://www.cve.org/ResourcesSupport/AllResources/CNARules
  title: CVE Numbering Authority (CNA) Operational Rules Version 4.0
  author: CVE Program / The MITRE Corporation
  last_modified: '2024-03-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: CVE JSON Schema 5.0 / CVE Program Charter
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

An **Authorized Data Publisher (ADP)** is a specialized organization officially designated by the CVE Program to enrich published CVE records by submitting data to dedicated `adp` containers without altering the authoring CNA's primary `cna` container[^cve-program].

# ADP Operational Role: The CISA Vulnrichment Pilot

CISA serves as the premier Authorized Data Publisher, operating the *Vulnrichment* program. When a CNA publishes a CVE record lacking severity metrics or weakness classifications, CISA ADP automatically analyzes the vulnerability and submits:
- **CVSS v3.1 and v4.0 Vectors**: Quantitative base scores.
- **CWE Identifiers**: Root cause weakness classifications.
- **SSVC Decision Trees**: Stakeholder-specific prioritization decisions.
- **KEV Catalog Status**: Flagging active exploitation.

# Related concepts
- [adpContainer (Authorized Data Publisher)](../programmes/cve/record-format/adp-container.md)
- [The CVE Program](../programmes/cve-program.md)
- [CISA Known Exploited Vulnerabilities (KEV) Catalog](../reference-data/kev.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
