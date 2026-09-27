---
type: Format
title: adpContainer (Authorized Data Publisher)
description: Non-destructive secondary enrichment container in CVE JSON Schema 5.0 allowing designated organizations like CISA and ENISA to publish independent scoring, CWE tags, and KEV metadata.
category: format
tags:
- cvd
- cve
- json-schema
- adp-container
- data-enrichment
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

The **`adp` Container** (`containers.adp`) is an architectural innovation introduced in CVE JSON Schema Version 5.0 that enables authorized secondary organizations—known as Authorized Data Publishers (ADPs)—to append authoritative enrichment metadata to published CVE Records without altering or overwriting the primary `cna` container[^cve-program]. Designated entities, such as the Cybersecurity and Infrastructure Security Agency (CISA) or the European Union Agency for Cybersecurity (ENISA), utilize `adp` containers to supply essential missing data, including Common Vulnerability Scoring System (CVSS) vectors, Common Weakness Enumeration (CWE) classifications, Known Exploited Vulnerabilities (KEV) operational notices, and affected version corrections[^iso-iec-29147].

By decoupling primary vendor attribution from third-party enrichment, the `adp` container establishes a federated, multi-perspective vulnerability intelligence ecosystem that preserves primary source integrity while satisfying the rigorous automation demands of global defenders.

# Technical Scope & Container Architecture

Within the CVE JSON 5.0 hierarchy, the `adp` property is an array of independent publisher blocks located under the root `containers` object:

```
containers
  ├── cna (Authoritative Primary Record)
  └── adp[] (Array of Authorized Data Publisher Enrichments)
       ├── adp[0]: CISA ADP (CVSS v3.1/v4.0, CWE, SSVC, KEV tags)
       └── adp[1]: ENISA EUVD ADP (EUVD references, NIS2 sector tags)
```

Each item in the `adp` array is structurally identical to the `cna` container, containing its own `providerMetadata`, `metrics`, `problemTypes`, `affected`, and `references` blocks.

### Architectural Advantages of the ADP Container

1. **Non-Destructive Coexistence**: An ADP cannot delete, overwrite, or mutate the vendor CNA's statements. Both datasets coexist within the same canonical JSON document, allowing consuming systems to choose whether to prioritize vendor-declared metrics or coordinator-assessed metrics[^cve-program].
2. **Filling Intelligence Gaps**: Many vendor CNAs publish sparse CVE Records containing only basic text descriptions and patch links, omitting CVSS scores or CWE identifiers. ADPs provide standardized automated scoring that vulnerability scanners require to compute risk prioritization scores[^cve-program].
3. **Multi-Jurisdictional Context**: Regional coordinators can attach localized compliance metadata (such as NIS2 critical sector applicability or national CSIRT advisories) without fragmenting the global identifier standard.

# CISA ADP Operational Profile

The CISA ADP program is the most prominent operational deployment of the `adp` container. Operating under a mandate to enrich newly published CVE Records, CISA's automated and analyst-assisted pipelines evaluate records against standard criteria:

- **Missing Metric Enrichment**: If a vendor CNA publishes a record without a CVSS vector, CISA ADP calculates and appends CVSS v3.1 and CVSS v4.0 scores.
- **CWE Assignment**: CISA analysts inspect the vulnerability description and patch diffs to attach precise CWE identifiers.
- **KEV Catalog Synchronization**: If a CVE is added to the CISA Known Exploited Vulnerabilities (KEV) catalog, the CISA ADP block flags the exploitation status and inserts mandatory remediation due dates for US federal agencies.
- **SSVC Decision Trees**: CISA attaches Stakeholder-Specific Vulnerability Categorization (SSVC) decision trees (e.g., `Track`, `Attend`, or `Act`).

### JSON 5.0 CISA ADP Container Example

```json
{
  "providerMetadata": {
    "orgId": "134c704f-9b21-4f2e-91b3-4a467353bcc0",
    "shortName": "CISA-ADP",
    "dateUpdated": "2026-02-20T12:00:00.000Z"
  },
  "title": "CISA ADP Vulnrichment",
  "problemTypes": [
    {
      "descriptions": [
        {
          "type": "CWE",
          "lang": "en",
          "cweId": "CWE-787",
          "description": "CWE-787: Out-of-bounds Write"
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
      "cvssV3_1": {
        "version": "3.1",
        "vectorString": "CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H",
        "baseScore": 9.8,
        "baseSeverity": "CRITICAL"
      }
    },
    {
      "other": {
        "type": "ssvc",
        "content": {
          "timestamp": "2026-02-20T11:45:00.000Z",
          "id": "CVE-2026-10492",
          "role": "CISA Coordinator",
          "options": [
            {"Exploitation": "active"},
            {"Automatable": "yes"},
            {"Technical Impact": "total"}
          ],
          "decision": "Act"
        }
      }
    }
  ],
  "tags": ["known-exploited-vulnerability"],
  "references": [
    {
      "url": "https://www.cisa.gov/known-exploited-vulnerabilities-catalog",
      "tags": ["government-resource"]
    }
  ]
}
```

# Applicability & Practical Implementation

### Parsing Multi-Container Records

Software vulnerability management platforms, security scanners, and SIEM/SOAR engines must implement deterministic resolution logic when ingesting CVE JSON 5.0 records with multiple containers:

```python
def resolve_cvss_score(cve_record):
    containers = cve_record.get("containers", {})
    
    # Priority 1: Check Authoritative CNA Container
    cna_metrics = containers.get("cna", {}).get("metrics", [])
    for metric in cna_metrics:
        if "cvssV4_0" in metric:
            return metric["cvssV4_0"]["baseScore"], "CNA-CVSS4"
        if "cvssV3_1" in metric:
            return metric["cvssV3_1"]["baseScore"], "CNA-CVSS3"
            
    # Priority 2: Fallback to Authorized Data Publisher (ADP) Enrichments
    for adp in containers.get("adp", []):
        for metric in adp.get("metrics", []):
            if "cvssV4_0" in metric:
                return metric["cvssV4_0"]["baseScore"], f"ADP-{adp['providerMetadata']['shortName']}-CVSS4"
            if "cvssV3_1" in metric:
                return metric["cvssV3_1"]["baseScore"], f"ADP-{adp['providerMetadata']['shortName']}-CVSS3"
                
    return None, "NO_METRICS_FOUND"
```

# Dates and Transitions

- **2023**: Pilot testing of the Authorized Data Publisher framework with CISA.
- **March 2024**: Full production deployment of CISA ADP ("Vulnrichment") across CVE Services, processing thousands of published records monthly.
- **2025–2026**: Integration of European Union Vulnerability Database (EUVD) ADP pipelines under ENISA oversight.

# Related concepts

- [Record Format Index](index.md)
- [cveMetadata Container](cve-tag-container.md)
- [CNA Container](cna-container.md)
- [Rejected Container](rejected-container.md)
- [Authorized Data Publisher Role](../../../roles/authorized-data-publisher.md)
- [CISA KEV Reference Data](../../../reference-data/kev.md)
- [SSVC Reference Data](../../../reference-data/ssvc.md)
- [EUVD Programme](../../euvd.md)

[^cve-program]: CVE Program / The MITRE Corporation, CVE Numbering Authority (CNA) Operational Rules Version 4.0, https://www.cve.org/ResourcesSupport/AllResources/CNARules
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
