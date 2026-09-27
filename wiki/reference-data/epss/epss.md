---
type: Metric
title: Exploit Prediction Scoring System (EPSS)
description: Data-driven predictive model estimating the statistical probability of
  real-world exploitation in the wild within 30 days to guide patch prioritization.
category: metric
tags:
- cvd
- metric
- scoring
- epss
- threat-intelligence
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: first-epss
  resource: https://www.first.org/epss
  title: Exploit Prediction Scoring System (EPSS)
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2023-03-07T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  provision: FIRST EPSS
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **Exploit Prediction Scoring System (EPSS)** is an open, data-driven machine learning framework managed by the Forum of Incident Response and Security Teams (FIRST) that predicts the likelihood that a software vulnerability will be exploited in the wild within the subsequent 30 calendar days[^first-epss]. While CVSS measures the fundamental technical severity of a vulnerability based on architectural attributes, EPSS evaluates dynamic threat landscape telemetry to estimate real-world adversary interest and operational exploitability.

By generating daily probability estimates for every published CVE ID, EPSS solves the "prioritization overload" problem faced by enterprise security teams, enabling organizations to focus immediate patching resources on the small fraction of vulnerabilities that adversaries are actively attempting to weaponize.

# Technical Scope & Predictive Model Mechanics

EPSS operates as an ensemble machine-learning model (specifically gradient-boosted decision trees) retrained continuously on vast corpora of vulnerability disclosures and threat telemetry:

```
+-----------------------------------------------------------------+
|                         EPSS Data Inputs                        |
+-----------------------------------------------------------------+
  ├── Vulnerability Metadata (CVE descriptions, age, CWE types)
  ├── Vendor & Product Characteristics (market presence, tech stack)
  ├── Public Exploit Availability (Metasploit, Exploit-DB, GitHub PoCs)
  ├── Threat Intel Feeds (Dark web chatter, underground forums)
  └── Intrusion Detection Telemetry (Honeypot hits, sensor alerts)
                                |
                                v
+-----------------------------------------------------------------+
|                   EPSS Machine Learning Engine                  |
+-----------------------------------------------------------------+
                                |
                                v
+-------------------------------+---------------------------------+
|  1. Probability Score (0.00000 - 1.00000 / 0% - 100%)           |
|     Likelihood of exploitation in the wild in the next 30 days  |
+-----------------------------------------------------------------+
|  2. Percentile Ranking (0.00000 - 1.00000 / 0% - 100%)          |
|     Relative ranking against all other published CVEs           |
+-----------------------------------------------------------------+
```

### The Two Core EPSS Metrics

Every daily EPSS evaluation produces two distinct numerical outputs:
1. **EPSS Probability Score**: A decimal between $0.00000$ and $1.00000$ representing the direct statistical probability that the vulnerability will be observed in active exploitation attempts within 30 days. For example, a score of `0.74215` denotes a 74.2% probability of imminent attack.
2. **EPSS Percentile**: A decimal between $0.00000$ and $1.00000$ indicating the proportion of all scored CVEs that have a lower probability score. For example, a percentile of `0.98500` indicates that the vulnerability scores higher than 98.5% of all cataloged vulnerabilities.

# Statistical Realities & The Remediation Paradigm

Empirical research conducted by FIRST and cybersecurity data scientists demonstrates the power of EPSS over traditional CVSS-only triage:

- **The Patching Paradox**: Out of hundreds of thousands of published CVEs, only approximately **5% to 7%** are ever actively exploited in the wild throughout their entire lifecycle.
- **CVSS Limitations**: Over 55% of all published vulnerabilities receive a CVSS score of 7.0 (High) or higher. Remediating every CVSS High and Critical vulnerability imposes unsustainable operational overhead while leaving critical unpatched zero-days exposed.
- **Efficiency and Coverage Gains**:
  - Remediating vulnerabilities with $\text{CVSS} \ge 7.0$ achieves high coverage but very low efficiency (wasting ~80% of remediation effort on bugs that are never attacked).
  - Combining $\text{CVSS} \ge 7.0$ with $\text{EPSS} \ge 0.20$ enables security teams to address over **85% of actively exploited vulnerabilities** while reducing total remediation patch volume by up to **75%**.

### Matrix: CVSS Severity vs. EPSS Probability

```
                       EPSS Exploitation Probability
                 Low (< 0.10)              High (>= 0.20)
           +-------------------------+-------------------------+
High /     | Deprioritized           | Immediate Action        |
Critical   | Severe bug, but no      | Severe bug under active |
(CVSS >= 7)| known exploit activity. | weaponization. Patch    |
           | Schedule routine patch. | immediately.            |
           +-------------------------+-------------------------+
Low /      | Lowest Priority         | Target of Opportunity   |
Medium     | Low severity, low       | Minor bug weaponized in |
(CVSS < 7) | exploit interest.       | exploit chains. Deploy  |
           | Backlog review.         | targeted mitigations.   |
           +-------------------------+-------------------------+
```

# Practical Implementation in PSIRT & Enterprise Operations

Organizations integrate EPSS through public REST APIs:
- **API Endpoint**: FIRST provides a publicly queryable API:
  ```http
  GET https://api.first.org/data/v1/epss?cve=CVE-2026-10492
  ```
  Response payload:
  ```json
  {
    "status": "OK",
    "status-code": 200,
    "data": [
      {
        "cve": "CVE-2026-10492",
        "epss": "0.89241",
        "percentile": "0.99412",
        "date": "2026-03-15"
      }
    ]
  }
  ```
- **SOAR / SIEM Pipeline**: Vulnerability management scanners automatically ingest the daily CSV dump (`https://epss.cyentia.com/epss_scores-current.csv.gz`) to recalculate ticket priority rankings every morning.

# Dates and Transitions

- **2019**: Initial conception and academic presentation of the EPSS model.
- **2021**: Release of EPSS v1.0 by FIRST.
- **2022**: EPSS v2.0 deployed, introducing expanded daily behavioral sensor data.
- **March 2023**: Launch of EPSS v3.0, yielding dramatic increases in predictive accuracy (F1 score) and lower false positive rates.

# Related concepts

- [Reference Data Index](index.md)
- [CVSS v3.1 Specification](../cvss/cvss-v3-1.md)
- [CVSS v4.0 Specification](../cvss/cvss-v4-0.md)
- [Stakeholder-Specific Vulnerability Categorization (SSVC)](../ssvc/ssvc.md)
- [CISA KEV Catalog](../kev/kev.md)
- [Triage and Validation Process](../../process/triage-and-validation.md)
- [Vendor PSIRT Role](../../roles/vendor-psirt.md)

[^first-epss]: Forum of Incident Response and Security Teams (FIRST), Exploit Prediction Scoring System (EPSS), https://www.first.org/epss
