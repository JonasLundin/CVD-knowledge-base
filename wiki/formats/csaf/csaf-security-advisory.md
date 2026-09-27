---
type: Format
title: CSAF Security Advisory Profile
description: Specialized vendor advisory profile under CSAF 2.0 detailing fixed vulnerabilities, affected and patched product versions, remediation actions, and CVSS severity metrics.
category: format
tags:
- cvd
- csaf
- advisory
- csaf-security-advisory
- vulnerability-remediation
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: oasis-csaf-2-0
  resource: https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html
  title: Common Security Advisory Framework (CSAF) Version 2.0
  author: OASIS Common Security Advisory Framework TC
  last_modified: '2022-11-09T00:00:00Z'
- id: iso-iec-29147
  resource: https://www.iso.org/standard/72311.html
  title: "ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2018-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: CSAF 2.0 Section 4.4
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CSAF Security Advisory Profile** (Section 4.4 of CSAF Version 2.0) is the definitive industry profile designed for software publishers, hardware manufacturers, and Product Security Incident Response Teams (PSIRTs) to release formal security advisories detailing remediated vulnerabilities[^oasis-csaf-2-0]. While the Base Profile defines universal document metadata, the Security Advisory Profile mandates rigorous technical relationships between identified vulnerabilities (CVEs), specific hardware/software product trees, authoritative severity scoring (CVSS), and actionable remediation measures (patches, workarounds, or upgrades)[^iso-iec-29147].

In modern DevSecOps and enterprise vulnerability management, CSAF Security Advisories eliminate the ambiguity of PDF or HTML security bulletins, empowering automated orchestrators to ingest vendor remediation data directly into patching workflows.

# Technical Scope & Profile Conformance

To conform to the Security Advisory Profile, a document must satisfy all requirements of the CSAF Base Profile plus specific mandatory assertions defined in CSAF 2.0 Section 4.4:

```
+-----------------------------------------------------------------+
| Mandatory Document Category                                     |
| document.category = "csaf_security_advisory"                    |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| Mandatory Product Tree (product_tree)                           |
| - Must define branches and full_product_names                   |
| - Must assign unique product_ids for affected & fixed targets   |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| Mandatory Vulnerabilities Array (vulnerabilities[])             |
| - At least one vulnerability object                             |
| - Must contain cve (or cwe/title)                               |
| - product_status: known_affected and/or fixed                   |
| - remediations: category, details, product_ids                  |
| - scores: CVSS v3.1 and/or CVSS v4.0 metrics                    |
+-----------------------------------------------------------------+
```

### Profile-Specific Conformance Assertions

| Schema Property | Requirement | Technical Conformance Rule |
| :--- | :--- | :--- |
| `document.category` | **Mandatory** | MUST be exactly `"csaf_security_advisory"`. |
| `product_tree` | **Mandatory** | The document must contain a fully articulated `product_tree` defining every referenced software/firmware artifact. |
| `vulnerabilities` | **Mandatory** | Array must contain at least one vulnerability object. |
| `vulnerabilities[].product_status` | **Mandatory** | Must populate at least one of `known_affected` or `fixed` with valid `product_id` strings defined in the `product_tree`. |
| `vulnerabilities[].remediations` | **Mandatory** | At least one remediation object must be provided. |
| `remediations[].category` | **Mandatory** | Enum: `"vendor_fix"`, `"workaround"`, `"mitigation"`, `"no_fix_planned"`, or `"none_available"`. |
| `remediations[].details` | **Mandatory** | Detailed human-readable explanation of the fix, installation instructions, or command syntax. |
| `remediations[].product_ids` | **Mandatory** | Array linking the remediation to the specific product IDs patched. |
| `vulnerabilities[].scores` | **Mandatory** | At least one scoring object containing standardized CVSS v3.1 or CVSS v4.0 vectors. |

# Complete Production-Grade CSAF Security Advisory Example

```json
{
  "document": {
    "category": "csaf_security_advisory",
    "csaf_version": "2.0",
    "title": "Security Update for Acme Cloud Gateway (Authentication Bypass)",
    "publisher": {
      "category": "vendor",
      "name": "Acme Security PSIRT",
      "namespace": "https://psirt.acme.example.com"
    },
    "tracking": {
      "id": "ACME-SA-2026-004",
      "current_release_date": "2026-03-12T10:00:00.000Z",
      "initial_release_date": "2026-03-12T10:00:00.000Z",
      "status": "final",
      "version": "1.0.0",
      "revision_history": [
        {
          "number": "1.0.0",
          "date": "2026-03-12T10:00:00.000Z",
          "summary": "Initial public release of security advisory."
        }
      ]
    }
  },
  "product_tree": {
    "full_product_names": [
      {
        "name": "Acme Cloud Gateway 5.1.0",
        "product_id": "PROD-ACG-510",
        "product_identification_helper": {
          "cpe": "cpe:2.3:a:acme:cloud_gateway:5.1.0:*:*:*:*:*:*:*"
        }
      },
      {
        "name": "Acme Cloud Gateway 5.1.2 (Patched)",
        "product_id": "PROD-ACG-512",
        "product_identification_helper": {
          "cpe": "cpe:2.3:a:acme:cloud_gateway:5.1.2:*:*:*:*:*:*:*"
        }
      }
    ]
  },
  "vulnerabilities": [
    {
      "cve": "CVE-2026-20891",
      "title": "Authentication Bypass in OAuth Token Validation Handler",
      "cwe": {
        "id": "CWE-287",
        "name": "Improper Authentication"
      },
      "product_status": {
        "known_affected": ["PROD-ACG-510"],
        "fixed": ["PROD-ACG-512"]
      },
      "scores": [
        {
          "cvss_v3": {
            "version": "3.1",
            "vectorString": "CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H",
            "baseScore": 9.8,
            "baseSeverity": "CRITICAL"
          }
        }
      ],
      "remediations": [
        {
          "category": "vendor_fix",
          "details": "Upgrade Acme Cloud Gateway instances to version 5.1.2 or later using the official update repository.",
          "product_ids": ["PROD-ACG-510"],
          "url": "https://downloads.acme.example.com/gateway/v5.1.2/update.tar.gz"
        }
      ]
    }
  ]
}
```

# Applicability & Practical Implementation

### Automation in Enterprise Vulnerability Management

CSAF Security Advisories streamline end-to-end vulnerability response:
1. **Automated Exposure Matching**: Enterprise asset managers parse the `known_affected` array against internal CMDB/inventory CPE coordinates. If `PROD-ACG-510` is detected, the vulnerability is flagged as active.
2. **Deterministic Remediation Ingestion**: Security orchestrators extract the `vendor_fix` remediation block and target download URL, automatically scheduling a maintenance window for upgrade.
3. **Audit Evidence**: Under Article 10 of the Cyber Resilience Act (CRA) and NIS2 Article 21, organizations retain ingested CSAF advisories as machine-readable evidence of timely vulnerability remediation[^iso-iec-29147].

# Dates and Transitions

- **November 2022**: CSAF 2.0 finalized, formalizing the Security Advisory Profile as the direct successor to the legacy Common Vulnerability Reporting Framework (CVRF 1.2).
- **2024–2026**: Transition mandate among European governmental and critical infrastructure vendors to supply advisories natively in CSAF 2.0 format.

# Related concepts

- [CSAF Profiles Index](index.md)
- [CSAF Base Profile](csaf-base.md)
- [CSAF VEX Profile](csaf-vex.md)
- [CSAF Informational Advisory](csaf-informational-advisory.md)
- [CSAF Security Incident Response](csaf-security-incident-response.md)
- [Advisory Publication Process](../../process/advisory-publication.md)
- [Vendor PSIRT Role](../../roles/vendor-psirt.md)
- [CVSS v3.1 Reference Data](../../reference-data/cvss/cvss-v3-1.md)
- [CVSS v4.0 Reference Data](../../reference-data/cvss/cvss-v4-0.md)

[^oasis-csaf-2-0]: OASIS Common Security Advisory Framework TC, Common Security Advisory Framework (CSAF) Version 2.0, https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
