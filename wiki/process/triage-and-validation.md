---
type: Procedure
title: 'Process: Triage, Reproduction, and Impact Assessment'
description: Initial verification of vulnerability reports, root cause analysis, severity
  assessment, and reproducibility confirmation.
category: procedure
tags:
- cvd
- process
- triage
- cvss
- iso-iec-30111
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: iso-iec-30111
  resource: https://www.iso.org/standard/72312.html
  title: "ISO/IEC 30111:2019 Information technology \u2014 Security techniques \u2014\
    \ Vulnerability handling processes"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2019-10-01T00:00:00Z'
- id: first-cvss-v4
  resource: https://www.first.org/cvss/v4-0/specification-document
  title: Common Vulnerability Scoring System (CVSS) Specification Document Version
    4.0
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2023-11-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: ISO/IEC 30111 Clause 6
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Triage, Reproduction, and Impact Assessment** is the technical investigation process conducted by a vendor's Product Security Incident Response Team (PSIRT) to verify the validity, exploitability, and scope of a reported vulnerability[^iso-iec-30111].

# Core Triage Stages

```
+-------------------+     +--------------------+     +---------------------+
| 1. Sanity Check   | ==> | 2. Lab Reproduction| ==> | 3. Root Cause & CWE |
| - Complete PoC?   |     | - Spin clean VM    |     | - Code audit        |
| - Supported vers? |     | - Execute exploit  |     | - Map weakness ID   |
+-------------------+     +--------------------+     +---------------------+
                                                                |
                                                                v
+-------------------+     +--------------------+     +---------------------+
| 6. Remediation    | <== | 5. SSVC & Priority | <== | 4. CVSS v4.0 Base   |
|    Assignment     |     | - Active threat?   |     |    Scoring          |
| - Engineering fix |     | - Set patch SLA    |     | - Vector generation |
+-------------------+     +--------------------+     +---------------------+
```

# Triage Criteria
- **Reproducibility**: Confirmation that the exploit reproduces reliably on supported software branches.
- **Severity Scoring**: Calculation of the official CVSS v4.0 vector[^first-cvss-v4].
- **Component Mapping**: Identification of exact upstream/downstream components using Package URLs.

# Related concepts
- [Intake Channels and Security.txt](intake-and-reporting.md)
- [Embargo Management and Coordination](embargo-management.md)
- [Common Vulnerability Scoring System (CVSS) v4.0](../reference-data/cvss/cvss-v4-0.md)
- [Common Weakness Enumeration (CWE)](../reference-data/cwe/cwe.md)

[^iso-iec-30111]: International Organization for Standardization (ISO) / IEC, ISO/IEC 30111:2019 Information technology — Security techniques — Vulnerability handling processes, https://www.iso.org/standard/72312.html
[^first-cvss-v4]: Forum of Incident Response and Security Teams (FIRST), Common Vulnerability Scoring System (CVSS) Specification Document Version 4.0, https://www.first.org/cvss/v4-0/specification-document
