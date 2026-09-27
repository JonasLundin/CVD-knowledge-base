---
type: Format
title: CSAF Informational Advisory Profile
description: Specialized CSAF 2.0 profile for publishing non-remediation security
  notices, defensive hardening guidelines, end-of-life warnings, and architecture
  advisories.
category: format
tags:
- cvd
- csaf
- advisory
- csaf-informational-advisory
- security-bulletin
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: oasis-csaf-2-0
  resource: https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
  title: Common Security Advisory Framework Version 2.0 (CSAF v2.0)
  author: OASIS Open
  last_modified: '2022-11-18T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: CSAF 2.0 Section 4.3
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CSAF Informational Advisory Profile** (Section 4.3 of CSAF Version 2.0) defines the standardized schema for security bulletins that provide strategic guidance, security hardening recommendations, deprecation notices, or threat awareness bulletins that are not tied to a specific newly fixed software vulnerability[^oasis-csaf-2-0]. While the Security Advisory Profile is reserved for specific code defect fixes and the VEX profile is reserved for exploitability assertions, the Informational Advisory Profile equips publishers to disseminate structured, machine-parsable security guidance to enterprise consumers[^oasis-csaf-2-0].

This profile ensures that non-patch security communications benefit from the same automated distribution channels, cryptographic validation, and tracking lifecycles as traditional vulnerability advisories.

# Technical Scope & Profile Conformance

Under Section 4.3 of CSAF 2.0, an Informational Advisory inherits all mandatory elements of the CSAF Base Profile and enforces specific structural rules:

```
+-----------------------------------------------------------------+
| Mandatory Document Category                                     |
| document.category = "csaf_informational_advisory"               |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| Mandatory Document Notes (document.notes[])                     |
| - Must contain at least one note detailing the advice/warning   |
| - Category: description, details, summary, or general           |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| Optional / Flexible Elements                                    |
| - product_tree (Optional: link advice to specific systems)     |
| - vulnerabilities (Optional: reference historical CVEs)         |
| - references (Recommended: links to guides, whitepapers)        |
+-----------------------------------------------------------------+
```

### Profile Conformance Assertions

| Schema Property | Requirement | Technical Conformance Rule |
| :--- | :--- | :--- |
| `document.category` | **Mandatory** | MUST be exactly `"csaf_informational_advisory"`. |
| `document.notes` | **Mandatory** | Array MUST contain at least one note object providing the substantive guidance or announcement. |
| `document.notes[].category`| **Mandatory** | Enum: `"description"`, `"details"`, `"summary"`, `"general"`, `"legal_disclaimer"`, etc. |
| `product_tree` | Optional | Permitted if the guidance applies to specific product families, architectures, or versions. |
| `vulnerabilities` | Optional | Permitted if the informational advisory discusses mitigation strategies for historical or industry-wide vulnerabilities. |

# Common Operational Use Cases

Organizations issue CSAF Informational Advisories in diverse operational contexts:

1. **Cryptographic Deprecation Notices**: Warning customers that legacy cipher suites (e.g., TLS 1.0, 3DES, or RSA keys under 2048 bits) will be disabled in upcoming major releases, requiring architectural updates.
2. **Hardening Best Practices**: Advising administrators on how to configure secure runtime isolation, enable strict firewall policies, or deploy multi-factor authentication (MFA) to mitigate emerging threat campaigns.
3. **End-of-Support / End-of-Life (EOL) Declarations**: Formal machine-readable notifications declaring that specific software lines will no longer receive security maintenance, fulfilling transparency mandates under the EU Cyber Resilience Act (CRA)[^oasis-csaf-2-0].
4. **Third-Party Ecosystem Advisories**: Guidance issued by cloud service providers explaining how customer workloads can defend against widespread zero-day campaigns impacting foundational internet protocols.

# Complete CSAF Informational Advisory Example

```json
{
  "document": {
    "category": "csaf_informational_advisory",
    "csaf_version": "2.0",
    "title": "Mandatory Migration to TLS 1.3 and Deprecation of Legacy Ciphers",
    "publisher": {
      "category": "vendor",
      "name": "Acme Cloud Infrastructure Security",
      "namespace": "https://security.acme.example.com"
    },
    "tracking": {
      "id": "ACME-INFO-2026-002",
      "current_release_date": "2026-01-15T09:00:00.000Z",
      "initial_release_date": "2026-01-15T09:00:00.000Z",
      "status": "final",
      "version": "1.0.0",
      "revision_history": [
        {
          "number": "1.0.0",
          "date": "2026-01-15T09:00:00.000Z",
          "summary": "Initial publication of cryptographic migration guidance."
        }
      ]
    },
    "notes": [
      {
        "category": "summary",
        "title": "Executive Overview",
        "text": "Acme Cloud Infrastructure will terminate support for TLS 1.0 and TLS 1.1 across all API endpoints effective June 1, 2026. Enterprise customers must ensure all client applications support TLS 1.3 to prevent connectivity disruptions."
      },
      {
        "category": "general",
        "title": "Recommended Action",
        "text": "Audit existing API integrations, update legacy cryptographic client libraries, and enforce TLS 1.3 in client connection pools."
      }
    ],
    "references": [
      {
        "category": "external",
        "summary": "Acme Cryptographic Hardening Guide",
        "url": "https://docs.acme.example.com/security/tls-migration-guide"
      }
    ]
  }
}
```

# Applicability & Practical Implementation

### Ingestion by Enterprise SecOps

CSAF Informational Advisories enable proactive security operations:
- **Policy Automation**: Security posture management tools parse informational advisories to automatically update internal baseline compliance benchmarks (e.g., flagging instances still negotiating deprecated cipher suites).
- **Automated Bulletin Distribution**: Enterprise communication bots automatically push informational notices to system administrators managing the relevant infrastructure domains.

# Dates and Transitions

- **November 2022**: CSAF 2.0 established the Informational Advisory profile, creating an unambiguous separation between code-patch advisories and operational security guidance.

# Related concepts

- [CSAF Profiles Index](index.md)
- [CSAF Base Profile](csaf-base.md)
- [CSAF Security Advisory](csaf-security-advisory.md)
- [CSAF VEX Profile](csaf-vex.md)
- [CSAF Security Incident Response](csaf-security-incident-response.md)
- [Advisory Publication Process](../../process/advisory-publication.md)
- [Vendor PSIRT Role](../../roles/vendor-psirt.md)

[^oasis-csaf-2-0]: OASIS Open, Common Security Advisory Framework Version 2.0 (CSAF v2.0), https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
