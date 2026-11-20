# Third-Party Documentation Index

This directory documents external components integrated or proposed for Wicofe.

## Architecture and policy
- [Dependency license policy 0.2](../policies/DEPENDENCY_LICENSE_POLICY_0.2.md) — GPL/AGPL prohibition, conditional LGPL approval and review of other license obligations.
- [Third-party intake and compliance architecture 0.1](THIRD_PARTY_INTAKE_ARCHITECTURE_0.1.md) — source provenance, license review, dependency inventory, security assessment, approval scope and SBOM integration.
- [Component record template](../COMPONENT_RECORD_TEMPLATE.md) — human-readable intake record for an individual dependency.

## Proposed component records
- [musl C library](../components/musl.md) — proposed Wlibc source foundation; project-level MIT evidence recorded, exact revision and component audit pending; not approved for import.

## Current audit records
- [CI action and cross-repository dependency inventory](../AUDIT.md) — upstream source commits, license evidence and strict audit findings.
- [Dependency review queue — 2026-11-16](../DEPENDENCY_REVIEW_QUEUE_2026-11-16.md) — rejected GPL host tools, LGPL-bearing alternatives, UNKNOWN identities, unapproved records and release blockers.

## Scope
- Component inventory and exact upstream provenance.
- Versions, commits, source integrity, and download records.
- License texts, notices, attribution, and redistribution obligations.
- Local patch tracking, security advisories, and maintenance status.
- Dependency and enabled-feature audits.
- SBOM and release inventory reconciliation.

## Ownership
This repository owns compliance/provenance records and third-party intake policy. [Wicofe-Port](https://github.com/Waizusora/Wicofe-Port) owns build recipes and integration patches. Component repositories own their use of dependencies and must link to the corresponding third-party record. [Wicofe-Build](https://github.com/Waizusora/Wicofe-Build) records build provenance; [Wicofe-Image](https://github.com/Waizusora/Wicofe-Image) assembles the final image inventory.

## Approval
A successful build or an open-source license alone is not approval. Apply the [dependency license policy](../policies/DEPENDENCY_LICENSE_POLICY_0.2.md): GPL and AGPL are prohibited; LGPL requires scoped review and approval; other licenses are allowed subject to compatibility and obligations review. Unknown or incomplete license evidence blocks approval.

- [Central documentation index](https://github.com/Waizusora/Wicofe-Doc/blob/main/INDEX.md)
- [Repository documentation map](https://github.com/Waizusora/Wicofe-Doc/blob/main/REPOSITORY_DOCUMENTATION_MAP.md)
