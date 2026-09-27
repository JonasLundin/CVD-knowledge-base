---
type: Metric
title: CISA Known Exploited Vulnerabilities (KEV) Catalog
description: Authoritative federal catalog of vulnerabilities known to be actively exploited in the wild, governed by CISA Binding Operational Directives.
category: metric
tags:
- reference-data
- kev
- cisa
- bod-26-04
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: cisa-kev
  resource: https://www.cisa.gov/known-exploited-vulnerabilities-catalog
  title: Known Exploited Vulnerabilities Catalog
  author: Cybersecurity and Infrastructure Security Agency (CISA)
  last_modified: '2026-06-10T00:00:00Z'
- id: cisa-bod-26-04
  resource: https://www.cisa.gov/news-events/directives/binding-operational-directive-26-04
  title: 'Binding Operational Directive 26-04: Advancing Federal Remediation of Exploited Vulnerabilities'
  author: Cybersecurity and Infrastructure Security Agency (CISA)
  last_modified: '2026-06-10T00:00:00Z'
x-cvd:
  jurisdiction: US
  authority_level: statutory
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CISA Known Exploited Vulnerabilities (KEV) Catalog** is an authoritative inventory of security flaws actively targeted and exploited by threat actors in the wild[^cisa-kev][^cisa-bod-26-04].

# Statutory Authority and Ingestion Criteria

## Federal Directives
Originally established under BOD 22-01 and modernized under **Binding Operational Directive 26-04**, KEV obligations are legally binding on all United States Federal Civilian Executive Branch (FCEB) agencies.

## Inclusion Thresholds
To be cataloged in KEV, an issue must meet three mandatory criteria:
1. Assigned a valid, active CVE ID.
2. Verified reliable evidence of active exploitation in the wild (observed campaigns or public weaponized proof-of-concept attacks).
3. Clear remediation action available (e.g., vendor patch, firmware upgrade, or documented mitigation).

# Related concepts
- [Reference Data Index](../index.md)
- [EPSS](../epss/epss.md)
- [SSVC](../ssvc/ssvc.md)

[^cisa-kev]: Cybersecurity and Infrastructure Security Agency (CISA), Known Exploited Vulnerabilities Catalog, https://www.cisa.gov/known-exploited-vulnerabilities-catalog
[^cisa-bod-26-04]: Cybersecurity and Infrastructure Security Agency (CISA), Binding Operational Directive 26-04: Advancing Federal Remediation of Exploited Vulnerabilities, https://www.cisa.gov/news-events/directives/binding-operational-directive-26-04
