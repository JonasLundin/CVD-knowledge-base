---
type: Procedure
title: 'Process: Advisory Publication and Patch Release'
description: Simultaneous public release of security advisory, CVE Record, and software
  patch or remediation guidance.
category: procedure
tags:
- cvd
- process
- advisory
- csaf
- cve-publishing
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: iso-iec-29147
  resource: https://www.iso.org/standard/72311.html
  title: "ISO/IEC 29147:2018 Information technology \u2014 Security techniques \u2014\
    \ Vulnerability disclosure"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2018-10-01T00:00:00Z'
- id: cve-program
  resource: https://www.cve.org/ResourcesSupport/AllResources/CNARules
  title: CVE Numbering Authority (CNA) Operational Rules Version 4.0
  author: CVE Program / The MITRE Corporation
  last_modified: '2024-03-01T00:00:00Z'
- id: oasis-csaf-2-0
  resource: https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html
  title: Common Security Advisory Framework (CSAF) Version 2.0
  author: OASIS Common Security Advisory Framework TC
  last_modified: '2022-11-09T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: ISO/IEC 29147 Clause 7
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Advisory Publication and Patch Release** is the culminating stage of the coordinated vulnerability disclosure lifecycle, in which the vendor PSIRT publicly releases remediation patches, publishes a security advisory, and transitions the assigned CVE ID to the `PUBLISHED` state[^iso-iec-29147][^cve-program].

# Synchronized Release Checklist

1. **Software Patch Deployment**: Binaries, packages, or container updates pushed to distribution mirrors and package registries.
2. **Machine-Readable Advisory**: Publishing an OASIS CSAF 2.0 Security Advisory (`csaf_security_advisory`) and VEX statement[^oasis-csaf-2-0].
3. **CVE Services Publication**: Executing a `PUT /api/cve/{cve_id}` API call to MITRE/CVE Services, transitioning the record from `RESERVED` to `PUBLISHED` with populated `cnaContainer`.
4. **Finder Acknowledgment**: Crediting the researcher in the advisory text according to prior agreement.

# Related concepts
- [CSAF 2.0 Security Advisory Profile](../formats/csaf/csaf-security-advisory.md)
- [Section 4: CVE Record Requirements and Publishing](../programmes/cve/cna-operational-rules/section-4-record-publishing.md)
- [cnaContainer (CNA Content)](../programmes/cve/record-format/cna-container.md)

[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^oasis-csaf-2-0]: OASIS Common Security Advisory Framework TC, Common Security Advisory Framework (CSAF) Version 2.0, https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html
