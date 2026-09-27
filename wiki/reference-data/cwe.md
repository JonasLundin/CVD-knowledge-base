---
type: Metric
title: Common Weakness Enumeration (CWE)
description: Community-developed taxonomy of software and hardware weakness types
  underlying vulnerabilities.
category: metric
tags:
- cvd
- metric
- cwe
- mitre
- weakness
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
x-cvd:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: MITRE CWE List
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Common Weakness Enumeration (CWE)** is an authoritative, community-developed dictionary and taxonomy of software and hardware weakness types[^cve-program]. Maintained by MITRE, CWE serves as a standard common language for identifying architectural flaws, coding bugs, and design defects that could lead to exploitable vulnerabilities.

In coordinated vulnerability disclosure and the CVE Record Format (JSON Schema 5.0), declaring one or more CWE identifiers in the `problemTypes` container is a core requirement for CNA compliance.

# Structure & Top-Level Categories

CWE is organized hierarchically into Views, Categories, and Weaknesses (Base, Variant, and Class level):
- **CWE-1000 (Research View)**: Complete taxonomy arranged by underlying mechanism of weakness.
- **CWE-699 (Software Development View)**: Weaknesses categorized by lifecycle phase (e.g., Memory Management, Authentication, Cryptography).
- **CWE-1194 (Hardware Design View)**: Weaknesses in physical hardware, silicon, and firmware (e.g., On-Chip Debug, Power Management).

### The CWE Top 25 Most Dangerous Software Weaknesses
An annually updated list calculating the most critical weaknesses based on real-world prevalence and severity in NVD/CVE records, consistently featuring:
1. `CWE-787`: Out-of-bounds Write
2. `CWE-79`: Improper Neutralization of Input During Web Page Generation (XSS)
3. `CWE-89`: SQL Injection
4. `CWE-416`: Use After Free
5. `CWE-78`: OS Command Injection

# Integration with CVE JSON Schema 5.0

In every published CVE record, CNAs record the root weakness inside `containers.cna.problemTypes`:

```json
{
  "problemTypes": [
    {
      "descriptions": [
        {
          "type": "CWE",
          "cweId": "CWE-787",
          "description": "CWE-787: Out-of-bounds Write",
          "lang": "en"
        }
      ]
    }
  ]
}
```

# Related concepts
- [CNA Container](../programmes/cve/record-format/cna-container.md)
- [Common Vulnerability Scoring System v4.0](cvss-v4-0.md)
- [Triage, Reproduction, and Impact Assessment](../process/triage-and-validation.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
