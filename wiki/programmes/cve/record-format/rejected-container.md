---
type: Format
title: rejectedContainer (Rejected Records)
description: Container populated when a CVE ID is revoked or invalidated, recording
  rejectedReasons and replacing CVE references.
category: format
tags:
- cvd
- cve
- json-schema
- rejected-container
status: draft
generated:
  by: agent:antigravity
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
  authority_level: standard
  instrument_status: in_force
  provision: CVE JSON Schema v5.0
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**rejectedContainer (Rejected Records)** in the CVE Record Format (JSON Schema Version 5)[^cve-program].

Container populated when a CVE ID is revoked or invalidated, recording rejectedReasons and replacing CVE references.

# Container Structure
Defines machine-readable schema constraints and parsing requirements for vulnerability data consumers.

# Related concepts
- [Record Format Index](index.md)
- [CVE Program Overview](../../cve-program.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
