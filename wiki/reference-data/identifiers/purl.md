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

**Package URL (purl)** is a standardized, ecosystem-agnostic URL specification used across software supply chain security and vulnerability databases to uniquely identify open-source and commercial software packages[^cve-schema-5-2-0].

# Specification Syntax and Ecosystem Role

A Package URL follows the canonical schema: `pkg:<type>/<namespace>/<name>@<version>?<qualifiers>#<subpath>`. By establishing consistent identifier syntax across package managers (e.g., npm, PyPI, Maven, Cargo, Debian), purl allows vulnerability coordination databases, CVE records, and VEX statements to unambiguously link security disclosures to affected components, eliminating naming ambiguities common in legacy text descriptions.

# Related concepts
- [Identifiers Index](index.md)
- [Common Platform Enumeration (CPE)](cpe.md)
- [Software Identification (SWID)](swid.md)

[^cve-schema-5-2-0]: CVE Project, CVE JSON Record Schema, Specification Version 5.2.0, https://cveproject.github.io/cve-schema
