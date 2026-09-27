---
type: Procedure
title: PSIRT Operational Workflows
description: Day-to-day vulnerability response operations, patch engineering, and cross-functional incident handling.
category: procedure
tags:
- process
- psirt
- operations
- remediation
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: first-psirt-services-framework
  resource: https://www.first.org/standards/frameworks/psirts/
  title: FIRST PSIRT Services Framework v1.1
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2021-03-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Product Security Incident Response Team (PSIRT) operations** encompass the structured activities undertaken by a technology vendor to triage, remediate, and disclose vulnerabilities in its products[^first-psirt-services-framework].

# Operational Lifecycle
1. **Intake**: Receiving reports via `security.txt`, PGP email, or portal.
2. **Verification & Scoring**: Confirming reproducible impact, assigning CVSS and CWE vectors.
3. **Engineering Fixes**: Collaborating with product engineering teams to create and test security patches.
4. **Advisory Publishing**: Releasing synchronized CSAF and CVE records.

# Related concepts
- [Advisory Lifecycle](advisory-lifecycle.md)
- [FIRST PSIRT Services Framework](../standards/first-psirt-services-framework.md)

[^first-psirt-services-framework]: Forum of Incident Response and Security Teams (FIRST), FIRST PSIRT Services Framework v1.1, https://www.first.org/standards/frameworks/psirts/
