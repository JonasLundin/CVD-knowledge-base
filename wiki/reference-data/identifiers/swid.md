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

**Software Identification (SWID) Tags** (standardized under ISO/IEC 19770-2) and their concise binary encoding **CoSWID** (RFC 9390) provide cryptographic XML and CBOR metadata files that record software identity, licensing, and installation state[^cve-schema-5-2-0].

# Integration in Vulnerability Management

In coordinated vulnerability disclosure and IT asset management, SWID tags deployed alongside commercial software allow automated vulnerability triage tools to discover installed software products reliably. In CVE Schema 5.2.0, SWID tags may be directly referenced within the `cna.affected.swid` structure, establishing cryptographic provenance between reported vulnerability advisories and managed operational environments.

# Related concepts
- [Identifiers Index](index.md)
- [Common Platform Enumeration (CPE)](cpe.md)
- [Package URL](purl.md)

[^cve-schema-5-2-0]: CVE Project, CVE JSON Record Schema, Specification Version 5.2.0, https://cveproject.github.io/cve-schema
