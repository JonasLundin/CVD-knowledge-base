---
type: Format
title: CSAF Security Incident Response Profile
description: Specialized CSAF 2.0 profile designed for CSIRTs and PSIRTs to issue early warnings, situational updates, and active exploitation advisories during ongoing cybersecurity incidents.
category: format
tags:
- cvd
- csaf
- advisory
- csaf-security-incident-response
- incident-response
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
  provision: CSAF 2.0 Section 4.2
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CSAF Security Incident Response Profile** (Section 4.2 of CSAF Version 2.0) is the specialized advisory profile engineered for Computer Security Incident Response Teams (CSIRTs), Product Security Incident Response Teams (PSIRTs), and national cybersecurity agencies to disseminate authoritative notices regarding active cybersecurity incidents, ongoing forensic investigations, and active exploitation campaigns[^oasis-csaf-2-0]. During the opening hours of a zero-day emergency or major supply chain compromise, vendors and coordinators cannot wait weeks for fully validated software patches before alerting defenders[^iso-iec-29147].

By relaxing the mandatory product tree and patch requirements enforced by the Security Advisory Profile, the Security Incident Response Profile equips responders to release rapid, machine-readable early warnings containing containment workarounds, Indicators of Compromise (IoCs), and forensic guidance.

# Technical Scope & Profile Conformance

Under Section 4.2 of CSAF 2.0, a Security Incident Response document conforms to strict structural requirements designed for high-velocity incident communication:

```
+-----------------------------------------------------------------+
| Mandatory Document Category                                     |
| document.category = "csaf_security_incident_response"           |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| Mandatory Incident Notes (document.notes[])                     |
| - Must contain at least one note detailing incident status      |
| - Category: description, details, summary, or general           |
+-------------------------------+---------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
| Rapid-Release Flexibility                                       |
| - product_tree (Optional: included if affected assets known)   |
| - vulnerabilities (Optional: included if CVE/CWE identified)   |
| - tracking.status: Commonly set to "interim" during active triage|
+-----------------------------------------------------------------+
```

### Profile Conformance Assertions

| Schema Property | Requirement | Technical Conformance Rule |
| :--- | :--- | :--- |
| `document.category` | **Mandatory** | MUST be exactly `"csaf_security_incident_response"`. |
| `document.notes` | **Mandatory** | Array MUST contain at least one note object describing the incident, threat actor activity, or temporary containment instructions. |
| `document.tracking.status`| **Mandatory** | Typically set to `"interim"` while investigations are underway, transitioning to `"final"` once root causes and patches are delivered. |
| `product_tree` | Optional | Can be omitted or progressively populated as affected versions are identified. |
| `vulnerabilities` | Optional | Can reference reserved CVE IDs or zero-day identifiers without requiring immediate patch remediations. |

# Operational Role During Incident Lifecycles

The Security Incident Response Profile operates as the primary communications vehicle across three critical incident phases:

1. **Initial Threat Alert (Hour 0–24)**:
   - A zero-day exploit is observed in the wild.
   - The PSIRT/CSIRT issues an initial CSAF document (`tracking.status: "interim"`) alerting constituents to active exploitation.
   - Immediate mitigations (e.g., blocking network ports, disabling affected services) are provided in `document.notes` or `vulnerabilities[].remediations` (category: `workaround`).
2. **Investigation & Scope Refinement (Days 2–7)**:
   - Forensic analysis isolates affected product lines.
   - The document is revised (`document.tracking.version` incremented), populating the `product_tree` with confirmed vulnerable product IDs.
3. **Transition to Remediation**:
   - Once permanent code fixes are engineered and verified, the organization publishes a full **CSAF Security Advisory**, referencing or superseding the original Incident Response bulletin[^iso-iec-29147].

# Complete CSAF Security Incident Response Example

```json
{
  "document": {
    "category": "csaf_security_incident_response",
    "csaf_version": "2.0",
    "title": "Active Exploitation of Zero-Day Vulnerability in Acme VPN Appliances",
    "publisher": {
      "category": "vendor",
      "name": "Acme Global Incident Response",
      "namespace": "https://response.acme.example.com"
    },
    "tracking": {
      "id": "ACME-IR-2026-001",
      "current_release_date": "2026-02-05T08:00:00.000Z",
      "initial_release_date": "2026-02-05T08:00:00.000Z",
      "status": "interim",
      "version": "1.0.0",
      "revision_history": [
        {
          "number": "1.0.0",
          "date": "2026-02-05T08:00:00.000Z",
          "summary": "Initial emergency incident alert regarding active exploitation."
        }
      ]
    },
    "notes": [
      {
        "category": "summary",
        "title": "Incident Overview",
        "text": "Acme PSIRT has identified targeted attacks actively exploiting an unpatched remote code execution vulnerability in Acme Enterprise VPN Gateway appliances. Threat actors are utilizing crafted TLS sessions to execute arbitrary commands."
      },
      {
        "category": "general",
        "title": "Emergency Containment Workaround",
        "text": "Immediately restrict administrative web access on port 8443 to internal management subnets and disable external portal access until an official firmware hotfix is released."
      }
    ],
    "references": [
      {
        "category": "external",
        "summary": "Threat Intelligence Advisory and IoCs",
        "url": "https://cert.europa.eu/publications/security-advisories/cert-eu-2026-01"
      }
    ]
  },
  "vulnerabilities": [
    {
      "cve": "CVE-2026-99001",
      "title": "Unauthenticated Remote Code Execution in VPN Gateway",
      "threats": [
        {
          "category": "exploit_status",
          "details": "Active exploitation in the wild confirmed by national CSIRTs."
        }
      ]
    }
  ]
}
```

# Applicability & Practical Implementation

### CSIRT & SOC Orchestration

Security Operations Centers (SOCs) leverage this profile for automated incident response:
- **Instant SOAR Triggering**: SOAR platforms detect `category: "csaf_security_incident_response"` and automatically trigger high-priority paging for incident response commanders.
- **Firewall Rule Ingestion**: Automated threat intelligence gateways extract workaround network configurations or external IP indicators directly from advisory references, blocking attack vectors in near-real-time.

# Dates and Transitions

- **November 2022**: Formal standardization in CSAF Version 2.0.
- **2024–2026**: Integrated into CSIRT Network operational playbooks under NIS2 Article 15 early warning mandates.

# Related concepts

- [CSAF Profiles Index](index.md)
- [CSAF Base Profile](csaf-base.md)
- [CSAF Security Advisory](csaf-security-advisory.md)
- [CSAF VEX Profile](csaf-vex.md)
- [CSAF Informational Advisory](csaf-informational-advisory.md)
- [Zero-Day Glossary](../../glossary/zero-day.md)
- [Coordinator Role](../../roles/coordinator.md)
- [Vendor PSIRT Role](../../roles/vendor-psirt.md)

[^oasis-csaf-2-0]: OASIS Common Security Advisory Framework TC, Common Security Advisory Framework (CSAF) Version 2.0, https://docs.oasis-open.org/csaf/csaf/v2.0/csaf-v2.0.html
[^iso-iec-29147]: International Organization for Standardization (ISO) / IEC, ISO/IEC 29147:2018 Information technology — Security techniques — Vulnerability disclosure, https://www.iso.org/standard/72311.html
