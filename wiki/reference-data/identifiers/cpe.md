---
type: Metric
title: Common Platform Enumeration (CPE)
description: Structured naming scheme for information technology systems, software, and packages governed by NIST.
category: metric
tags:
- reference-data
- identifiers
- cpe
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

**Common Platform Enumeration (CPE)** is a standardized method of naming classes of applications, operating systems, and hardware devices, widely utilized in CVE Record affected fields[^cve-schema-5-2-0].

# Syntax Structure (CPE 2.3 Formatted String)
`cpe:2.3:[part]:[vendor]:[product]:[version]:[update]:[edition]:[language]:[sw_edition]:[target_sw]:[target_hw]:[other]`
- `part`: `a` (application), `o` (operating system), or `h` (hardware).

# Related concepts
- [Package URL (purl)](purl.md)
- [CVE ID Syntax](cve-id-syntax.md)

[^cve-schema-5-2-0]: CVE Project, CVE JSON Record Schema, Specification Version 5.2.0, https://cveproject.github.io/cve-schema
