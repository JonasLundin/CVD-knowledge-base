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

**Common Platform Enumeration (CPE)** is a standardized structured naming scheme managed by NIST for identifying classes of operating systems, hardware devices, and software applications within vulnerability disclosures[^cve-schema-5-2-0].

# Technical Mechanics and Schema Integration

CPE represents product configurations through Uniform Resource Identifiers (CPE 2.2) or formatted string bindings (CPE 2.3), utilizing the `cpe:2.3:[part]:[vendor]:[product]:[version]:...` syntax. In vulnerability disclosure workflows and CVE records, CPE identifiers provide machine-readable asset matching, enabling automated scanners to cross-reference installed system software against known exploited vulnerability catalogs (such as CISA KEV) and automated advisory alerts.

# Related concepts
- [Identifiers Index](index.md)
- [Package URL](purl.md)
- [CVE Record Format](../../programmes/cve/record-format/index.md)

[^cve-schema-5-2-0]: CVE Project, CVE JSON Record Schema, Specification Version 5.2.0, https://cveproject.github.io/cve-schema
