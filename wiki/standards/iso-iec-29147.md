---
type: Standard
title: ISO/IEC 29147:2018 Vulnerability Disclosure Standard
description: International benchmark standard specifying guidelines for vendors and
  coordinators on receiving, investigating, and disclosing vulnerabilities.
category: standard
tags:
- cvd
- standard
- iso-iec-29147
- vulnerability-disclosure
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
x-cvd:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: ISO/IEC 29147:2018
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**ISO/IEC 29147:2018 (Information technology — Security techniques — Vulnerability disclosure)** is the international standard governing how vendors, coordinators, and vulnerability finders exchange vulnerability information[^iso-iec-29147].

ISO/IEC 29147 establishes the operational bridge between external security researchers and vendor incident response teams, defining standardized communication channels, disclosure policies, and public advisory formats.

# Clause-by-Clause Structural Overview

```
+-------------------------------------------------------------------+
|                   ISO/IEC 29147 CLAUSE BREAKDOWN                  |
+-------------------------------------------------------------------+
| Clause 5: VENDOR VULNERABILITY DISCLOSURE CAPABILITIES           |
| - Establishing published vulnerability disclosure policies        |
| - Secure intake channels (PGP, web portals, RFC 9116 security.txt)|
| - Designating internal PSIRT operational roles                    |
+-------------------------------------------------------------------+
| Clause 6: INTERACTION BETWEEN FINDERS AND VENDORS                 |
| - Receipt acknowledgment (SLA: 24 to 72 hours)                    |
| - Report validation, clarification, and scope confirmation        |
| - Mutual agreement on embargo windows and coordination dates      |
+-------------------------------------------------------------------+
| Clause 7: VULNERABILITY ADVISORY PUBLICATION                      |
| - Publishing remediation advice, workarounds, and patches         |
| - Advisory content elements (CVE ID, CVSS vector, affected vers)  |
| - Finder credit, attribution, and acknowledgments                 |
+-------------------------------------------------------------------+
| Clause 8: COORDINATOR ROLES & MULTI-PARTY HANDLING                |
| - Intermediary functions when vendors are unresponsive or disputed|
| - Synchronized disclosure timelines across multiple vendors       |
+-------------------------------------------------------------------+
```

# Mandatory Elements in a Vulnerability Advisory (Clause 7.3)
When publishing an advisory under ISO/IEC 29147, the vendor must include:
1. **Advisory Identifier**: Unique tracking number and standard CVE identifier.
2. **Product Details**: Exhaustive list of affected product versions, hardware architectures, and operating environments.
3. **Vulnerability Description**: High-level explanation of the root cause flaw without weaponized exploit payloads.
4. **Impact Assessment**: Common Vulnerability Scoring System (CVSS) vector and qualitative impact (e.g. Remote Code Execution, Privilege Escalation).
5. **Remediation Details**: Clear instructions on downloading patches, upgrade paths, or temporary configuration workarounds.
6. **Researcher Acknowledgment**: Express credit to the finder (if permitted by the researcher).

# Related concepts
- [ISO/IEC 30111: Vulnerability Handling Processes](iso-iec-30111.md)
- [Intake Channels and Security.txt](../process/intake-and-reporting.md)
- [Advisory Publication and Patch Release](../process/advisory-publication.md)
- [Vendor PSIRT Role](../roles/vendor-psirt.md)

[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
