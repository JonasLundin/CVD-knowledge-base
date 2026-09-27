---
type: Format
title: CVE Record ADP Container
description: Supplemental container populated by Authorized Data Publishers (ADPs) under CVE JSON Schema 5.2.0.
category: format
tags:
- cve
- record-format
- adp-container
- schema-5-2-0
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: cve-schema-5-2-0
  resource: https://cveproject.github.io/cve-schema
  title: CVE JSON Record Schema, Specification Version 5.2.0
  author: CVE Project
  last_modified: '2025-10-29T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: containers.adp
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **ADP Container** (`containers.adp`) allows Authorized Data Publishers (such as CISA or community consortia) to enrich existing CVE Records without modifying or overwriting the authoritative CNA Container[^cve-schema-5-2-0].

# Enrichment Capabilities

1. **Independent Metrics**: Appending supplementary CVSS 4.0 or SSVC scores.
2. **KVE Annotations**: Flagging inclusion in CISA's Known Exploited Vulnerabilities catalog.
3. **CPE Disambiguation**: Adding structured Common Platform Enumeration (CPE) match criteria.
4. **Alternative References**: Augmenting vendor advisories with third-party analytical reports.

# Related concepts
- [Record Format Index](index.md)
- [CNA Container](cna-container.md)
- [Authorized Data Publisher Role](/roles/authorized-data-publisher.md)

[^cve-schema-5-2-0]: CVE Project, CVE JSON Record Schema, Specification Version 5.2.0, https://cveproject.github.io/cve-schema
