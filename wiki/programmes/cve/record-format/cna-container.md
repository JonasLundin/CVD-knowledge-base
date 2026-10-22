---
type: Format
title: CVE Record CNA Container
description: Primary vulnerability container populated by the assigning CNA under CVE JSON Schema 5.2.0.
category: format
tags:
- cve
- record-format
- cna-container
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
  provision: containers.cna
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CNA Container** (`containers.cna`) is the authoritative payload section of a CVE Record created and maintained by the assigning CVE Numbering Authority under CVE JSON Schema 5.2.0[^cve-schema-5-2-0].

# Core Fields

1. **Provider Metadata (`providerMetadata`)**: Identifies the assigning CNA's Organization ID (`orgId`) and update timestamp (`dateUpdated`).
2. **Descriptions (`descriptions`)**: Multi-lingual technical descriptions (§5.2.4).
3. **Affected Products (`affected`)**: Product identifiers, vendor names, version ranges, platforms, and default status (`affected`, `unaffected`, `unknown`).
4. **Problem Types (`problemTypes`)**: Standardized CWE identifiers and text descriptions.
5. **References (`references`)**: Public URLs with advisory tags.
6. **Metrics (`metrics`)**: CVSS v3.1, CVSS v4.0, or SSVC scoring objects.
7. **Tags (`tags`)**: Standardized flags including `unsupported-when-assigned`, `exclusively-hosted-service`, and `disputed`.

# Related concepts
- [Record Format Index](index.md)
- [ADP Container](adp-container.md)
- [CVE Metadata](cve-metadata.md)

[^cve-schema-5-2-0]: CVE Project, CVE JSON Record Schema, Specification Version 5.2.0, https://cveproject.github.io/cve-schema
