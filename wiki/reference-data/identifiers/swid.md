---
type: Metric
title: Software Identification (SWID) Tags
description: ISO/IEC 19770-2 standardized XML tags recording lifecycle metadata for installed software products.
category: metric
tags:
- reference-data
- identifiers
- swid
- iso-19770-2
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
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Software Identification (SWID) Tags** (ISO/IEC 19770-2) provide authoritative, cryptographically signed metadata about installed software components[^cve-schema-5-2-0].

# Role in Vulnerability Management
- **Asset Verification**: Ingested by automated asset scanners to identify installed software versions accurately.
- **CVE Cross-Referencing**: Correlated with CVE JSON Schema affected objects and CSAF advisories.

# Related concepts
- [Common Platform Enumeration (CPE)](cpe.md)
- [Package URL (purl)](purl.md)

[^cve-schema-5-2-0]: CVE Project, CVE JSON Record Schema, Specification Version 5.2.0, https://cveproject.github.io/cve-schema
