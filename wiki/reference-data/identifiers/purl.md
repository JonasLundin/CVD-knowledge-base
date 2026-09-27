---
type: Metric
title: Package URL (purl) Specification
description: Standardized URL string syntax for locating and identifying software packages reliably across ecosystems.
category: metric
tags:
- reference-data
- identifiers
- purl
- packaging
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

**Package URL (purl)** standardizes how software packages are identified across programming package managers (e.g., npm, maven, pypi, cargo, debian)[^cve-schema-5-2-0].

# Syntax Scheme
`pkg:<type>/<namespace>/<name>@<version>?<qualifiers>#<subpath>`
- Examples: `pkg:npm/%40angular/animation@12.3.1`, `pkg:maven/org.apache.logging.log4j/log4j-core@2.14.1`.

# Related concepts
- [Common Platform Enumeration (CPE)](cpe.md)
- [SWID Tags](swid.md)

[^cve-schema-5-2-0]: CVE Project, CVE JSON Record Schema, Specification Version 5.2.0, https://cveproject.github.io/cve-schema
