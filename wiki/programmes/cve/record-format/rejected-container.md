---
type: Format
title: rejectedContainer (Rejected Records)
description: Structural container and validation schema populated in CVE JSON 5.0 when a CVE ID is revoked or rejected, documenting formal rejection reasons and superseded-by links.
category: format
tags:
- cvd
- cve
- json-schema
- rejected-container
- invalidation
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

The **`rejectedContainer`** represents the specialized payload structure within CVE JSON Schema Version 5.0 deployed when a CVE Identifier is formally revoked, invalidated, or retired[^cve-program]. Under CNA Operational Rules Version 4.0, a CVE ID cannot be silently deleted or erased from the global registry once issued. Instead, records that are identified as duplicates, determined not to be security vulnerabilities, or assigned in violation of scoping boundaries must be transitioned to the `REJECTED` lifecycle state[^iso-iec-29147].

The `rejectedContainer` preserves historical transparency, documents the technical justification for invalidation, prevents duplicate re-assignment of the retired ID, and provides machine-readable cross-references directing security tools to the authoritative replacement identifiers.

# Technical Scope & Schema Structure

When `cveMetadata.state` is set to `"REJECTED"`, the root `containers.cna` object must conform to the rejected record schema constraints rather than the standard publication schema:

```
containers
  └── cna
       ├── providerMetadata (Mandatory: orgId, shortName, dateUpdated)
       ├── rejectedReasons (Mandatory: array of language-tagged explanation objects)
       └── replacedBy (Optional: array of superseding CVE ID strings)
```

### Schema Specification & Rules

| Property Name | Data Type | Mandatory? | Technical Description & Constraints |
| :--- | :--- | :--- | :--- |
| `providerMetadata` | Object | **Mandatory** | Contains `orgId`, `shortName`, and `dateUpdated` for the rejecting authority. |
| `rejectedReasons` | Array | **Mandatory** | Array of objects with `lang` (e.g., `"en"`) and `value`. Must provide a factual explanation of why the record was invalidated. |
| `replacedBy` | Array | Conditional | Array of valid CVE ID strings (e.g., `["CVE-2026-54321"]`). Required when the rejection is due to duplicate assignment or identifier merging. |

# Common Rejection Scenarios

Under Section 6 of the CNA Operational Rules, records are transitioned to `REJECTED` under well-defined procedural scenarios:

### 1. Duplicate Assignment (Cross-CNA or Intra-CNA Collision)
Two CNAs independently assign separate CVE IDs to the same underlying vulnerability (e.g., an upstream open-source flaw assigned by both a coordinator CNA and an OS distribution CNA). The later or downstream identifier is rejected, and `replacedBy` points to the primary upstream identifier[^cve-program].

### 2. Not a Vulnerability (Design Feature or Misconfiguration)
Following technical re-evaluation or vendor dispute adjudication, the reported behavior is proven to be intentional design functionality, an operational misconfiguration without unsafe defaults, or a theoretical issue unexploitable across any supported environment[^cve-program].

### 3. Researcher Retraction
The original finder discovers a fatal flaw in the proof-of-concept (e.g., test harness artifact or corrupted sandbox) and formally withdraws the report prior to or immediately following initial publication.

### 4. Out-of-Scope Assignment Error
A CNA mistakenly assigned a CVE ID to third-party commercial software outside its authorized charter. The record is rejected with instructions pointing consumers to the appropriate vendor CNA or Root.

# Complete JSON 5.0 Rejected Record Example

Below is a complete, production-grade CVE JSON 5.0 document demonstrating a duplicate assignment rejection:

```json
{
  "dataType": "CVE_RECORD",
  "dataVersion": "5.0",
  "cveMetadata": {
    "cveId": "CVE-2026-11892",
    "assignerOrgId": "82542658-c272-4020-bc12-72d8d615f760",
    "assignerShortName": "distro-cna",
    "state": "REJECTED",
    "dateReserved": "2026-01-20T10:00:00.000Z",
    "datePublished": "2026-02-01T15:00:00.000Z",
    "dateUpdated": "2026-02-05T09:30:00.000Z",
    "dateRejected": "2026-02-05T09:30:00.000Z"
  },
  "containers": {
    "cna": {
      "providerMetadata": {
        "orgId": "82542658-c272-4020-bc12-72d8d615f760",
        "shortName": "distro-cna",
        "dateUpdated": "2026-02-05T09:30:00.000Z"
      },
      "rejectedReasons": [
        {
          "lang": "en",
          "value": "This record was assigned in error for a vulnerability in the libnetwork package that had already been assigned CVE-2026-0814 by the upstream project CNA. This identifier has been rejected to prevent duplicate vulnerability tracking."
        }
      ],
      "replacedBy": [
        "CVE-2026-0814"
      ]
    }
  }
}
```

# Applicability & Practical Implementation

### Automated Ingestion Logic for Vulnerability Scanners

Vulnerability scanning platforms and dependency management tools must implement explicit handling for `REJECTED` records:
- **Alert Suppression**: When a scanner encounters `state: "REJECTED"`, it must immediately clear or suppress alerts associated with that CVE ID to avoid raising false positives during client compliance audits.
- **Alias Resolution**: If `replacedBy` is populated, the scanner should automatically update its asset risk graphs to link any discovered software versions to the replacement CVE ID.

# Dates and Transitions

- **CNA Rules Version 4.0 (March 2024)**: Standardized the machine-readable `rejectedReasons` array and `replacedBy` pointers in CVE JSON 5.0, phasing out the legacy unstructured text prefixes (such as `"** REJECT **"`).

# Related concepts

- [Record Format Index](index.md)
- [cveMetadata Container](cve-tag-container.md)
- [CNA Container](cna-container.md)
- [ADP Container](adp-container.md)
- [Section 6: Dispute Resolution](../cna-operational-rules/section-6-dispute-resolution.md)
- [Section 3: Assignment Rules](../cna-operational-rules/section-3-id-assignment-rules.md)
- [Secretariat Role](../../../roles/secretariat.md)
- [CNA Role](../../../roles/cna.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
