---
type: Role
title: 'Role: Vendor PSIRT'
description: Product Security Incident Response Team responsible for receiving, analyzing,
  and fixing vulnerabilities in vendor products.
category: role
tags:
- cvd
- role
- psirt
- first
- vendor
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
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: FIRST PSIRT Services Framework
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Vendor PSIRT** (Product Security Incident Response Team) is the designated operational team within a software or hardware vendor responsible for managing the lifecycle of vulnerabilities impacting the vendor's products, services, and digital offerings[^iso-iec-29147].

# Core Capabilities under the FIRST Framework

Under the FIRST PSIRT Services Framework:
- **Intake & Receipt**: Maintaining `/.well-known/security.txt` and secure PGP intake inboxes.
- **Technical Triage**: Laboratory reproduction, CVSS severity scoring, and CWE weakness classification.
- **Remediation Management**: Partnering with core engineering squads to author, test, and backport security patches.
- **CVE Administration**: Operating as an authorized CVE Numbering Authority (CNA) to assign CVE IDs[^cve-program].
- **Advisory & VEX Issuance**: Generating machine-readable CSAF 2.0 advisories.

# Related concepts
- [Finder (Security Researcher)](finder.md)
- [CVE Numbering Authority (CNA)](cna.md)
- [Triage, Reproduction, and Impact Assessment](../process/triage-and-validation.md)
- [Advisory Publication and Patch Release](../process/advisory-publication.md)

[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
