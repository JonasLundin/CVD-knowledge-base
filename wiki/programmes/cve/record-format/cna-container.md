---
type: Format
title: cnaContainer (CNA Content)
description: Authoritative technical payload container submitted by the assigning CVE Numbering Authority, detailing affected versions, weakness classifications, severity metrics, and remediation guidance in CVE JSON 5.0.
category: format
tags:
- cvd
- cve
- json-schema
- cna-container
- vulnerability-data
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
  authority_level: standard
  instrument_status: in_force
  provision: CVE JSON Schema v5.0
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **`cna` Container** (`containers.cna`) represents the primary, authoritative technical payload of a published CVE Record within the CVE JSON Schema Version 5.0 framework[^cve-program]. Authored directly by the designated CVE Numbering Authority (CNA) responsible for the vulnerability's scope, the `cna` container articulates the definitive description of the security defect, structured matrices of affected and unaffected software versions, weakness classifications using Common Weakness Enumeration (CWE), severity scoring vectors, remediation references, and researcher acknowledgements[^iso-iec-29147].

In modern vulnerability intelligence and software supply chain management, the `cna` container replaces ambiguous, free-text advisories with standardized, parser-friendly schema objects that feed automated dependency scanners, Software Bill of Materials (SBOM) analyzers, and security operations centers worldwide.

# Technical Scope & Schema Structure

The `cna` container is nested under `containers.cna` within the root CVE Record. It is bound by rigid structural constraints enforced during API submission:

```
containers
  └── cna
       ├── providerMetadata (Mandatory: orgId, shortName, dateUpdated)
       ├── title (Recommended: human-readable headline)
       ├── descriptions (Mandatory: language-tagged text strings)
       ├── affected (Mandatory: vendor, product, versions[], platforms)
       ├── problemTypes (Recommended: CWE identifiers and names)
       ├── metrics (Recommended: CVSS v3.1, CVSS v4.0, SSVC objects)
       ├── references (Mandatory: URLs, tags, advisory links)
       ├── solutions / workarounds (Optional: remediation steps)
       ├── credits (Optional: finder and coordinator attribution)
       ├── timeline (Optional: chronological discovery/disclosure milestones)
       └── tags (Optional: "disputed", "unsupported-when-assigned")
```

### Key Schema Elements & Specifications

| Field Name | Type | Constraint | Description & Technical Rules |
| :--- | :--- | :--- | :--- |
| `providerMetadata` | Object | **Mandatory** | Contains `orgId` (UUIDv4 of the submitting CNA), `shortName`, and `dateUpdated` (ISO 8601 UTC timestamp). |
| `descriptions` | Array | **Mandatory** | Array of objects containing `lang` (BCP 47 language code, e.g., `"en"`) and `value` (unformatted string detailing flaw, trigger condition, and operational impact). |
| `affected` | Array | **Mandatory** | Array of affected product blocks. Each block must specify `vendor`, `product`, and a `versions` array. |
| `affected[].versions`| Array | **Mandatory** | Version definitions. Each entry requires `version` and `status` (`affected`, `unaffected`, or `unknown`). Can define `lessThan`, `lessThanOrEqual`, and `versionType` (`semver`, `git`, `custom`). |
| `references` | Array | **Mandatory** | Array of reference objects. Each requires `url` (valid RFC 3986 URI) and optional `tags` (e.g., `["vendor-advisory", "patch"]`). |
| `problemTypes` | Array | **Recommended** | Standardized categorization of flaws, containing `descriptions[].cweId` (e.g., `"CWE-89"`) and description text. |
| `metrics` | Array | **Recommended** | Standardized scoring data. May contain `cvssV3_1`, `cvssV4_0`, or other structured metrics objects with valid vector strings. |

# The `affected` Matrix Specification

One of the most powerful advancements in CVE JSON 5.0 is the formalization of machine-readable version logic within the `affected` array:

### Version Range Operators
- **`status`**: Defines the exposure state for the specified version or boundary. Acceptable values:
  - `"affected"`: Confirmed vulnerable to exploitation.
  - `"unaffected"`: Confirmed patched, remediated, or inherently immune.
  - `"unknown"`: Status unverified or disputed.
- **`versionType`**: Declares the versioning syntax used to evaluate range comparisons. Common types include `"semver"` (Semantic Versioning 2.0.0), `"git"` (Git commit hash revisions), `"rpm"`, `"maven"`, or `"custom"`.
- **`lessThan` / `lessThanOrEqual`**: Defines an open-ended or inclusive upper bound for a vulnerable series.

```json
"affected": [
  {
    "vendor": "Kubernetes",
    "product": "kube-apiserver",
    "defaultStatus": "unaffected",
    "versions": [
      {
        "version": "1.28.0",
        "status": "affected",
        "lessThan": "1.28.6",
        "versionType": "semver"
      },
      {
        "version": "1.29.0",
        "status": "affected",
        "lessThan": "1.29.2",
        "versionType": "semver"
      }
    ]
  }
]
```

# Authoritative CNA Payload Example

Below is a complete, valid JSON Schema 5.0 `cna` container demonstrating multi-vector metrics, CWE problem types, and structured references:

```json
{
  "providerMetadata": {
    "orgId": "134c704f-9b21-4f2e-91b3-4a467353bcc0",
    "shortName": "cisa",
    "dateUpdated": "2026-02-18T16:20:00.000Z"
  },
  "title": "SQL Injection in OpenSource ERP Portal",
  "descriptions": [
    {
      "lang": "en",
      "value": "Improper neutralization of special elements in SQL commands ('SQL Injection') in OpenSource ERP Portal version 3.0.0 through 3.4.1 allows remote authenticated administrative users to execute arbitrary SQL commands via the report_id parameter."
    }
  ],
  "affected": [
    {
      "vendor": "ERP Foundation",
      "product": "ERP Portal",
      "defaultStatus": "unaffected",
      "versions": [
        {
          "version": "3.0.0",
          "status": "affected",
          "lessThan": "3.4.2",
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
          "cweId": "CWE-89",
          "description": "CWE-89: Improper Neutralization of Special Elements used in an SQL Command"
        }
      ]
    }
  ],
  "metrics": [
    {
      "format": "CVSS",
      "scenarios": [
        {
          "lang": "en",
          "value": "GENERAL"
        }
      ],
      "cvssV4_0": {
        "version": "4.0",
        "vectorString": "CVSS:4.0/AV:N/AC:L/AT:N/PR:H/UI:N/VC:H/VI:H/VA:H/SC:N/SI:N/SA:N",
        "baseScore": 8.6,
        "baseSeverity": "HIGH"
      }
    }
  ],
  "references": [
    {
      "url": "https://erp.example.org/security/advisories/ERP-2026-04",
      "tags": ["vendor-advisory", "patch"]
    },
    {
      "url": "https://github.com/erp-foundation/portal/commit/a8c7b3e942f1",
      "tags": ["patch"]
    }
  ],
  "credits": [
    {
      "lang": "en",
      "value": "Alice Smith of Cyber Research Labs",
      "type": "finder"
    }
  ]
}
```

# Operational Rules & Data Integrity

Under Section 4 of the CNA Operational Rules:
- **Exclusivity of CNA Authority**: The `cna` container can only be modified by the assigning CNA or by the Secretariat during formal dispute resolution. Other organizations cannot alter these fields[^cve-program].
- **Accuracy Obligation**: The assigning CNA is responsible for the technical veracity of its statements. If version ranges are misstated or descriptions omit critical attack vectors, the CNA must issue an update via `PUT /api/cve/{cve_id}/cna`[^cve-program].
- **Anti-Duplication**: References must point to authoritative primary sources, avoiding circular cross-references to automated vulnerability scrapers.

# Dates and Transitions

- **October 2022**: Formal release of CVE JSON Schema 5.0 specification.
- **March 1, 2024**: Full production enforcement; older CVE JSON 4.0 structures deprecated across all assigning CNAs.

# Related concepts

- [Record Format Index](index.md)
- [cveMetadata Container](cve-tag-container.md)
- [ADP Container](adp-container.md)
- [Rejected Container](rejected-container.md)
- [Section 4: Record Publishing](../cna-operational-rules/section-4-record-publishing.md)
- [CWE Reference Data](../../../reference-data/cwe/cwe.md)
- [CVSS v4.0 Reference Data](../../../reference-data/cvss/cvss-v4-0.md)
- [CNA Role](../../../roles/cna.md)
- [Vendor PSIRT Role](../../../roles/vendor-psirt.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
