---
type: Rule
title: 'Section 4: CVE Record Requirements and Publishing'
description: Mandatory data schema elements, CVE JSON 5.0 format compliance, lifecycle states, and publishing timelines under CNA Operational Rules v4.0.
category: rule
tags:
- cvd
- cve
- cna-rules
- section-4-record-publishing
- cve-json-5
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
  title: "ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2018-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: Section 4
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Section 4: CVE Record Requirements and Publishing** establishes the mandatory data specifications, formatting rules, lifecycle state transitions, and publishing timelines governing CVE Records under CNA Operational Rules Version 4.0[^cve-program]. With the transition of the CVE Program to a real-time, automated synchronization architecture powered by CVE Services and CVE JSON Schema 5.0, Section 4 ensures that every published record delivers actionable, high-fidelity technical data to the global vulnerability ecosystem[^iso-iec-29147].

Under Section 4, a CVE ID is not merely an alphanumeric tag; it is an authoritative, machine-readable record that documents affected software versions, weakness classifications, remediation references, and impact assessments.

# Technical Scope & CVE Record Lifecycle

A CVE identifier moves through three distinct lifecycle states managed within the central CVE Registry:

```
+-----------------------------------------------------------------+
|                         1. RESERVED                             |
|  - CVE ID allocated to a CNA via CVE Services API               |
|  - Details strictly embargoed; no public technical metadata     |
+-------------------------------+---------------------------------+
                                |
             +------------------+------------------+
             | Disclosed                           | Invalidated /
             v                                     v
+-------------------------------+   +-------------------------------+
|         2. PUBLISHED          |   |          3. REJECTED          |
|  - Populated CNA container    |   |  - Withdrawn / duplicate /    |
|  - Mandatory JSON 5.0 fields  |   |    not a vulnerability        |
|  - Publicly browsable & synced|   |  - Mandatory rejection reason |
+-------------------------------+   +-------------------------------+
```

### Lifecycle State Definitions
1. **RESERVED**: The CVE ID has been allocated from the program's global numbering pool to an authorized CNA. The identifier is held under embargo while vulnerability validation, patch authoring, or coordination proceeds. Only the CNA's `orgId` and reservation timestamp are visible.
2. **PUBLISHED**: The vulnerability has been made public, and the CNA has populated and submitted an authoritative CVE Record conforming to CVE JSON Schema 5.0. The record is globally accessible via the CVE Services API and web portals.
3. **REJECTED**: The CVE ID is retired because it was reserved in error, determined not to be a vulnerability, duplicate of an existing CVE ID, or withdrawn by the assigner. A rejected record must contain an explicit explanation and cross-references to any superseding CVE IDs.

# Mandatory Data Elements (CVE JSON Schema 5.0)

Under Section 4, every record transitioned to `PUBLISHED` status must satisfy the structural schema constraints of the **CNA Container** (`containers.cna`)[^cve-program]:

| Schema Element | Requirement Level | Technical Specification & Constraints |
| :--- | :--- | :--- |
| `providerMetadata` | **Mandatory** | Contains `orgId` (UUID of the publishing CNA), `shortName`, and `dateUpdated` (ISO 8601 timestamp). |
| `descriptions` | **Mandatory** | Array of language-tagged strings (e.g., `lang: "en"`). Must provide a clear explanation of the defect, affected component, attack vector, and potential impact. |
| `affected` | **Mandatory** | Array defining `vendor`, `product`, and `versions`. Each version entry must declare `status` (`affected`, `unaffected`, or `unknown`), `version`, and optionally `lessThan` boundaries. |
| `references` | **Mandatory** | Array of valid URLs pointing to official vendor advisories, bug trackers, commit hashes, or technical bulletins. |
| `problemTypes` | **Recommended** | Structured array of Common Weakness Enumeration identifiers (e.g., `CWE-79`) and textual descriptions. |
| `metrics` | **Recommended** | Standardized severity vectors and numerical scores, including CVSS v3.1, CVSS v4.0, or SSVC decision trees. |
| `solutions` | **Optional** | Remediation instructions, official patch versions, or temporary mitigations/workarounds. |
| `credits` | **Optional** | Acknowledgement of the security researcher, finder, or coordinator. |
| `tags` | **Optional** | Standardized tags including `disputed`, `unsupported-when-assigned`, or `exclusively-hosted-service`. |

### JSON 5.0 CNA Container Code Example

```json
{
  "dataType": "CVE_RECORD",
  "dataVersion": "5.0",
  "cveMetadata": {
    "cveId": "CVE-2026-12345",
    "assignerOrgId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "state": "PUBLISHED",
    "dateReserved": "2026-01-15T09:00:00.000Z",
    "datePublished": "2026-03-10T14:00:00.000Z",
    "dateUpdated": "2026-03-10T14:00:00.000Z"
  },
  "containers": {
    "cna": {
      "providerMetadata": {
        "orgId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
        "shortName": "acme-corp",
        "dateUpdated": "2026-03-10T14:00:00.000Z"
      },
      "title": "Improper Input Validation in Acme Gateway",
      "descriptions": [
        {
          "lang": "en",
          "value": "Improper input validation in Acme Gateway before version 4.2.1 allows an unauthenticated remote attacker to cause denial of service via crafted HTTP headers."
        }
      ],
      "affected": [
        {
          "vendor": "Acme Corporation",
          "product": "Acme Gateway",
          "defaultStatus": "unaffected",
          "versions": [
            {
              "version": "4.0.0",
              "status": "affected",
              "lessThan": "4.2.1",
              "versionType": "semver"
            }
          ]
        }
      ],
      "problemTypes": [
        {
          "descriptions": [
            {
              "type": "CWE",
              "lang": "en",
              "cweId": "CWE-20",
              "description": "CWE-20 Improper Input Validation"
            }
          ]
        }
      ],
      "references": [
        {
          "url": "https://security.acme.example.com/advisories/ACME-2026-001",
          "tags": ["vendor-advisory"]
        }
      ]
    }
  }
}
```

# Publication Timelines & Operational Rules

Section 4 mandates strict timeliness standards for transitioning records:

1. **Mandatory Publication Window**: When a vulnerability is made public (via vendor bulletin, patch release, public bug tracker, conference presentation, or researcher blog), the CNA MUST publish the populated CVE Record to the CVE Services within **24 hours to a maximum of 5 business days**[^cve-program].
2. **Prohibition of "Stale RESERVED" Status**: CNAs must never leave publicly disclosed vulnerabilities in `RESERVED` status. Neglecting to populate disclosed CVE IDs undermines global telemetry and asset-management operations[^cve-program].
3. **Continuous Updating Obligation**: If initial disclosure omitted affected version ranges, or if subsequent investigation reveals additional impacted branches or corrected CVSS scores, the CNA must submit an updated record via `PUT /api/cve/{cve_id}/cna` without delay.

# Practical Implementation & PSIRT Workflow

For a Vendor PSIRT or CNA:
- **Automation Pipeline**: Modern PSIRTs integrate CVE record publication into their CI/CD and release automation pipelines. When release management signs an advisory tag, a webhook generates both the CSAF advisory and the CVE JSON 5.0 payload, submitting the payload directly to `https://cveawg.mitre.org/api/cve/{cve_id}/cna`.
- **Pre-flight Schema Validation**: The PSIRT validates the payload against the official `cve_record_schema.json` prior to HTTP transmission, ensuring HTTP 200 OK acceptance and preventing publication delays.

# Dates and Transitions

- **March 1, 2024**: CNA Rules v4.0 made CVE JSON Schema 5.0 and direct CVE Services API submission strictly mandatory. Legacy submissions via flat GitHub pull requests and JSON 4.0 were fully deprecated.
- **CVE Services 2.1**: Introduced real-time schema validation and role-based access controls for CNAs and ADPs.

# Related concepts

- [CNA Operational Rules Index](index.md)
- [Section 1: Program Overview](section-1-program-overview.md)
- [Section 3: CVE ID Assignment Rules](section-3-id-assignment-rules.md)
- [Section 5: Embargo Management](section-5-embargo-management.md)
- [Section 6: Dispute Resolution](section-6-dispute-resolution.md)
- [CNA Container](../record-format/cna-container.md)
- [ADP Container](../record-format/adp-container.md)
- [Rejected Container](../record-format/rejected-container.md)
- [CSAF Security Advisory](../../../formats/csaf/csaf-security-advisory.md)
- [Advisory Publication Process](../../../process/advisory-publication.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
