---
type: Format
title: CSAF Vulnerability Exploitability eXchange (VEX) Profile
description: Specialized machine-readable profile under CSAF 2.0 asserting actual exploitability status (known_not_affected, known_affected, fixed, under_investigation) to eliminate SBOM false positives.
category: format
tags:
- cvd
- csaf
- advisory
- csaf-vex
- vex
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
  provision: CSAF 2.0 Section 4.5
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CSAF Vulnerability Exploitability eXchange (VEX) Profile** (Section 4.5 of CSAF Version 2.0) is the standardized machine-readable profile that allows software vendors, device manufacturers, and open-source projects to publish authoritative assertions regarding whether a specific vulnerability is actually exploitable within their products[^oasis-csaf-2-0]. While Software Bill of Materials (SBOM) documents identify every upstream library and dependency embedded in a product, the mere presence of a vulnerable library does not necessarily render the product exploitable[^iso-iec-29147].

By communicating machine-actionable statuses such as `known_not_affected` alongside standardized technical justifications (e.g., dead code elimination, compiler flags, or sandboxing), CSAF VEX eliminates massive volumes of false positives, saving security teams thousands of hours of unnecessary manual investigation.

# Technical Scope & The Four VEX Statuses

The CSAF VEX Profile revolves around four mutually exclusive product exploitability statuses declared within `vulnerabilities[].product_status`:

```
                       +---------------------------------------+
                       |          Vulnerability (CVE)          |
                       +-------------------+-------------------+
                                           |
         +-----------------+---------------+---------------+-----------------+
         |                 |                               |                 |
         v                 v                               v                 v
+-----------------+ +-----------------+             +-------------+   +---------------+
| under_          | | known_          |             | known_      |   | fixed         |
| investigation   | | not_affected    |             | affected    |   |               |
| (Triage in      | | (Immune /       |             | (Confirmed  |   | (Remediated   |
| progress)       | | Unexploitable)  |             | Vulnerable) |   | in build)     |
+-----------------+ +--------+--------+             +------+------+   +---------------+
                             |                             |
                             v                             v
                    +-----------------+           +-----------------+
                    | Justification & |           | Remediation &   |
                    | Impact Note     |           | Workaround      |
                    +-----------------+           +-----------------+
```

### The Four VEX Status Definitions

1. **`under_investigation`**: The publisher is aware of the vulnerability and is actively conducting code review and testing to determine whether the product is affected.
2. **`known_not_affected`**: The publisher has completed technical analysis and determined that the product is NOT vulnerable to exploitation.
3. **`known_affected`**: The publisher confirms that the product contains the vulnerable code and that an exploit path exists under reachable configurations.
4. **`fixed`**: The product version previously contained the flaw, but the vulnerability has been remediated in the specified release.

# Standardized Justifications for `known_not_affected`

Under Section 4.5 of CSAF 2.0, if a publisher designates a product as `known_not_affected`, the document MUST provide either a standardized machine-readable `justification` enum or an explicit `impact` note explaining why the product is immune:

| Justification Enum | Technical Definition & Practical Scenario |
| :--- | :--- |
| `component_not_present` | The reported third-party library or component is completely absent from the shipping binary or runtime container. |
| `vulnerable_code_not_present` | The vendor bundles a modified, forked, or stripped version of the library where the vulnerable function or file was intentionally removed prior to compilation. |
| `vulnerable_code_not_in_execute_path`| The vulnerable function exists in the binary, but no code execution path in the application can ever reach or invoke that function during runtime (dead code or uncalled API). |
| `vulnerable_code_cannot_be_controlled_by_adversary`| The vulnerable function is invoked, but all user inputs are strictly sanitized or constrained by upstream architectural boundaries, preventing adversarial control. |
| `inline_mitigations_already_exist`| Compiler-level protections (e.g., ASLR, stack canaries, FORTIFY_SOURCE) or kernel sandboxing mechanisms prevent the vulnerability from being triggered or exploited. |

# Complete Production CSAF VEX Example

```json
{
  "document": {
    "category": "csaf_vex",
    "csaf_version": "2.0",
    "title": "VEX Status for Acme Microservices (Log4j Evaluation)",
    "publisher": {
      "category": "vendor",
      "name": "Acme Product Security",
      "namespace": "https://psirt.acme.example.com"
    },
    "tracking": {
      "id": "ACME-VEX-2026-019",
      "current_release_date": "2026-02-10T14:00:00.000Z",
      "initial_release_date": "2026-02-10T14:00:00.000Z",
      "status": "final",
      "version": "1.0.0",
      "revision_history": [
        {
          "number": "1.0.0",
          "date": "2026-02-10T14:00:00.000Z",
          "summary": "Formal VEX declaration for CVE-2021-44228."
        }
      ]
    }
  },
  "product_tree": {
    "full_product_names": [
      {
        "name": "Acme Data Collector Container 2.4",
        "product_id": "CSAFPID-ACME-DC-24",
        "product_identification_helper": {
          "purl": "pkg:oci/acme-data-collector@sha256:d8a7c2b64ef93108c5e?"
        }
      }
    ]
  },
  "vulnerabilities": [
    {
      "cve": "CVE-2021-44228",
      "title": "Log4Shell JNDI Remote Code Execution",
      "product_status": {
        "known_not_affected": ["CSAFPID-ACME-DC-24"]
      },
      "threats": [
        {
          "category": "impact",
          "details": "Although log4j-core is present in the container classpath, Acme Data Collector enforces Java 17 runtime constraints and JVM property log4j2.formatMsgNoLookups=true, rendering JNDI lookup interpolation impossible.",
          "product_ids": ["CSAFPID-ACME-DC-24"]
        }
      ],
      "flags": [
        {
          "label": "vulnerable_code_cannot_be_controlled_by_adversary",
          "product_ids": ["CSAFPID-ACME-DC-24"]
        }
      ]
    }
  ]
}
```

# Applicability & Practical Implementation

### Automation in DevSecOps & Regulatory Compliance

CSAF VEX is critical for high-velocity software supply chain environments:
1. **Automated Scanner Suppression**: CI/CD security scanners ingest the product SBOM and match CVEs. Concurrently, the pipeline pulls the vendor's CSAF VEX document. If a detected dependency matches `known_not_affected`, the alert is automatically downgraded from Critical to Informational, preventing build breakage.
2. **Regulatory Compliance (CRA & US Executive Order 14028)**: Under the Cyber Resilience Act, manufacturers must provide vulnerability handling transparency. CSAF VEX provides the standard format required to justify why unpatched third-party CVEs in dependencies pose no risk to end consumers[^iso-iec-29147].

# Dates and Transitions

- **November 2022**: CSAF 2.0 formally defined the VEX profile, harmonizing with CISA VEX minimum requirements.
- **2024–2026**: Broad deployment across European container registries, package managers, and SBOM analysis engines.

# Related concepts

- [CSAF Profiles Index](index.md)
- [CSAF Base Profile](csaf-base.md)
- [CSAF Security Advisory](csaf-security-advisory.md)
- [CSAF Informational Advisory](csaf-informational-advisory.md)
- [CSAF Security Incident Response](csaf-security-incident-response.md)
- [Vendor PSIRT Role](../../roles/vendor-psirt.md)
- [Coordinated Vulnerability Disclosure Glossary](../../glossary/coordinated-vulnerability-disclosure.md)

[^oasis-csaf-2-0]: OASIS Common Security Advisory Framework TC, Common Security Advisory Framework (CSAF) Version 2.0, https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
