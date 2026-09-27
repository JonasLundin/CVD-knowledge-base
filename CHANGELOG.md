# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- CNA Operational Rules Version 4.2.0 coverage across Sections 1 through 6 with leaf citations (§4.5.1.3, §4.5.1.4, §5.2.4).
- Formal coverage of ENISA as a CVE Root (November 20, 2025) and European Vulnerability Database (EUVD) under NIS2 Article 12(2).
- Distinct national CVD frameworks, designated CSIRTs, and safe-harbour analyses for all 27 EU Member States and 3 EEA countries.
- Missing core concepts: CVE Services, Top-Level Roots, CNA Types, CNA-LR, OpenVEX, CycloneDX VEX, CPE, purl, SWID, ETSI TR 103 838, FIRST PSIRT Services Framework, safe harbour, bug bounty interfaces, PSIRT operations, and advisory lifecycles.
- Standardized tags support under CVE JSON Schema 5.2.0 (`unsupported-when-assigned`, `exclusively-hosted-service`, `disputed`).

### Changed
- Replaced 145 paywalled ISO 29147 citations across non-ISO pages with verified primary sources in `sources.yaml`.
- Replaced templated placeholder jurisdiction pages with authentic designated CSIRTs, statutory acts, and safe-harbour assessments.
- Corrected statutory references from NIS2 Article 11 to Article 12 across all documents.
- Updated CSAF VEX example to use neutral placeholder `CVE-YYYY-NNNNN` and added `vulnerable_code_not_in_execute_path` justification.
- Modernized KEV reference to CISA Binding Operational Directive 26-04.
- Updated `coverage.yaml` (`coverage_status: partial`, gates for 2 record containers).

## [0.1.0] - 2026-09-27
- Initial baseline release of Coordinated Vulnerability Disclosure knowledge base.
