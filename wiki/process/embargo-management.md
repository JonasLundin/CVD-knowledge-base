---
type: Procedure
title: 'Process: Embargo Management and Coordination'
description: Establishing mutually agreed embargo windows (typically 90 days) during
  remediation development.
category: procedure
tags:
- cvd
- process
- embargo
- cna-rules
- coordination
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
- id: iso-iec-29147
  resource: https://www.iso.org/standard/72311.html
  title: "ISO/IEC 29147:2018 Information technology \u2014 Security techniques \u2014\
    \ Vulnerability disclosure"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2018-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: CVE CNA Operational Rules Section 5
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Embargo Management** is the formal coordination window during which vulnerability details and assigned CVE identifiers are kept strictly confidential between the finder, vendor PSIRT, and designated coordinators while remediation patches are engineered and tested[^cve-program][^iso-iec-29147].

# Industry Standard Windows

- **Standard Window (90 Days)**: Widely adopted standard (e.g., Google Project Zero, CERT/CC), granting the vendor 90 calendar days to release a fix before public disclosure.
- **Grace Periods (14 Days)**: If a vendor has a validated patch scheduled for release within 14 days following the 90-day deadline, finders typically grant a short extension.
- **Zero-Day / Active Exploitation Exception**: If reliable evidence confirms the vulnerability is being actively exploited in the wild, the embargo is shortened immediately (typically to **7 days** or immediate coordinated advisory).

# Downstream Sharing under Embargo

Vendors may share pre-release patches and embargoed CVE IDs with downstream partners and multi-vendor working groups under strict Non-Disclosure Agreements (NDAs) to facilitate synchronized release.

# Related concepts
- [Section 5: Embargo Management and Coordination](../programmes/cve/cna-operational-rules/section-5-embargo-management.md)
- [Multi-Party Vulnerability Coordination](multi-party-coordination.md)
- [Advisory Publication and Patch Release](advisory-publication.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
