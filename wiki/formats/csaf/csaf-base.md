---
type: Format
title: CSAF Base Profile
description: Baseline document architecture and foundation profile of the Common Security Advisory Framework (CSAF) Version 2.0, establishing core metadata, tracking, publisher, and product tree requirements.
category: format
tags:
- cvd
- csaf
- advisory
- csaf-base
- schema
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
  provision: CSAF 2.0 Section 4.1
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CSAF Base Profile** constitutes the foundational specification of the Common Security Advisory Framework (CSAF) Version 2.0, standardized by the OASIS CSAF Technical Committee[^oasis-csaf-2-0]. Serving as the structural baseline for all specialized advisory profiles (such as Security Advisories, VEX documents, and Incident Response notices), the Base Profile establishes the mandatory document envelope, cryptographic publisher identity, lifecycle tracking history, distribution rules, and product identification trees[^iso-iec-29147].

By standardizing core metadata and product relationship graphs into strict JSON schemas, the Base Profile enables enterprise vulnerability scanners, national CSIRTs, and automated incident response tools to parse, validate, and index heterogeneous security disclosures without requiring proprietary custom adapters.

# Technical Scope & Schema Architecture

A valid CSAF 2.0 document adhering to the Base Profile contains three top-level schema elements: `document`, `product_tree`, and `vulnerabilities`:

```
csaf_document
  ├── document (Mandatory)
  │    ├── category (String: profile identifier)
  │    ├── csaf_version (Constant: "2.0")
  │    ├── publisher (vendor, coordinator, discoverer, other)
  │    ├── title (Human-readable document title)
  │    ├── tracking (id, dates, status, revision_history)
  │    ├── distribution (TLP, text restrictions)
  │    └── notes / references (Optional acknowledgements & links)
  │
  ├── product_tree (Optional in Base; Mandatory in downstream profiles)
  │    ├── branches[] (Hierarchical product decomposition)
  │    ├── full_product_names[] (product_id, name, CPE, PURL, hashes)
  │    └── relationships[] (default_component_of, optional_component_of)
  │
  └── vulnerabilities[] (Optional in Base; populated in specific profiles)
```

### Core Schema Requirements (Section 4.1 Conformance)

| Schema Path | Mandated? | Type | Validation & Conformance Rule |
| :--- | :--- | :--- | :--- |
| `document.category` | **Yes** | String | Identifies document type; non-empty string without whitespace padding. |
| `document.csaf_version` | **Yes** | String | Constant literal; MUST be exactly `"2.0"`. |
| `document.title` | **Yes** | String | Definitive human-readable title of the advisory document. |
| `document.publisher` | **Yes** | Object | Must contain `category` (`vendor`, `coordinator`, `discoverer`, `other`), `name`, and `namespace` (URI/URL). |
| `document.tracking.id` | **Yes** | String | Globally unique tracking identifier assigned by the publisher. |
| `document.tracking.status`| **Yes** | Enum | Document release state: `"draft"`, `"final"`, or `"interim"`. |
| `document.tracking.version`| **Yes** | String | Version string conforming to Semantic Versioning (SemVer) or integer series. |
| `document.tracking.revision_history`| **Yes** | Array | Chronological array of revisions containing `date`, `number`, and `summary`. |
| `document.tracking.initial_release_date`| **Yes** | DateTime | ISO 8601 UTC timestamp of original document publication. |
| `document.tracking.current_release_date`| **Yes** | DateTime | ISO 8601 UTC timestamp of current revision. |

# The CSAF Product Tree

The `product_tree` is the formal mechanism within CSAF used to define products, components, hardware modules, and container images referenced in vulnerability statements:

- **Product IDs (`product_id`)**: Unique internal alphanumeric tokens (e.g., `CSAFPID-0001`) referenced throughout the document's vulnerability blocks.
- **Product Identification Helpers**:
  - **Common Platform Enumeration (CPE)**: Well-formed CPE 2.2 or CPE 2.3 identifiers (e.g., `cpe:2.3:a:acme:gateway:4.2.0:*:*:*:*:*:*:*`).
  - **Package URL (PURL)**: Standardized specification for open-source package coordinates (e.g., `pkg:golang/github.com/gin-gonic/gin@v1.9.1`).
  - **Cryptographic Hashes**: SHA-256 or SHA-512 hashes verifying software artifacts.
  - **SBOM URLs**: Pointers to external Software Bill of Materials (SPDX or CycloneDX documents).

```json
"product_tree": {
  "branches": [
    {
      "category": "vendor",
      "name": "Acme Networks",
      "branches": [
        {
          "category": "product_name",
          "name": "Acme Edge Firewall",
          "branches": [
            {
              "category": "product_version",
              "name": "3.8.1",
              "product": {
                "name": "Acme Edge Firewall 3.8.1",
                "product_id": "CSAFPID-0001",
                "product_identification_helper": {
                  "cpe": "cpe:2.3:a:acme:edge_firewall:3.8.1:*:*:*:*:*:*:*"
                }
              }
            }
          ]
        }
      ]
    }
  ]
}
```

# Applicability & Practical Implementation

### Profile Conformance Hierarchy

All specialized CSAF profiles inherit the schema rules of the Base Profile:
- **Security Incident Response Profile**: Sets `document.category: "csaf_security_incident_response"` and requires summary notes.
- **Informational Advisory Profile**: Sets `document.category: "csaf_informational_advisory"` for general guidance.
- **Security Advisory Profile**: Sets `document.category: "csaf_security_advisory"`, mandating `product_tree`, `vulnerabilities`, and `remediations`.
- **VEX Profile**: Sets `document.category: "csaf_vex"`, mandating exploitability statuses (`known_affected`, `known_not_affected`, etc.) and justifications.

### Automated Feed Distribution

CSAF 2.0 defines standardized web distribution mechanisms under the `.well-known/csaf/` directory:
- `provider-metadata.json`: Declares the publisher's cryptographic signing keys (OpenPGP), feed endpoints, and CSAF role.
- `index.txt` / `changes.csv`: Enables vulnerability aggregators to poll and mirror advisories incrementally.

# Dates and Transitions

- **November 2022**: Formal publication of OASIS CSAF Version 2.0 as an approved Committee Specification.
- **2024–2026**: Broad international adoption across European Union agencies (BSI, ENISA) and integration into EU Cyber Resilience Act (CRA) compliance tooling.

# Related concepts

- [CSAF Profiles Index](index.md)
- [CSAF Security Advisory](csaf-security-advisory.md)
- [CSAF VEX Profile](csaf-vex.md)
- [CSAF Informational Advisory](csaf-informational-advisory.md)
- [CSAF Security Incident Response](csaf-security-incident-response.md)
- [Vendor PSIRT Role](../../roles/vendor-psirt.md)
- [Advisory Publication Process](../../process/advisory-publication.md)

[^oasis-csaf-2-0]: OASIS Common Security Advisory Framework TC, Common Security Advisory Framework (CSAF) Version 2.0, https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
