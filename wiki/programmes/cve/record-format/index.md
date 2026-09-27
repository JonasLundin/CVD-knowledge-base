# CVE Record Format

CVE Record Format 5.2.0 containers, required and recommended fields, tags, ADP containers.

## Concepts

- [adpContainer (Authorized Data Publisher)](adp-container.md) — Non-destructive secondary enrichment container in CVE JSON Schema 5.0 allowing designated organizations like CISA and ENISA to publish independent scoring, CWE tags, and KEV metadata.
- [cnaContainer (CNA Content)](cna-container.md) — Authoritative technical payload container submitted by the assigning CVE Numbering Authority, detailing affected versions, weakness classifications, severity metrics, and remediation guidance in CVE JSON 5.0.
- [cveMetadata Container](cve-tag-container.md) — Top-level envelope and metadata container in CVE JSON Schema 5.0 tracking cveId, assignerOrgId, lifecycle state, publication timestamps, and revision history.
- [rejectedContainer (Rejected Records)](rejected-container.md) — Structural container and validation schema populated in CVE JSON 5.0 when a CVE ID is revoked or rejected, documenting formal rejection reasons and superseded-by links.
