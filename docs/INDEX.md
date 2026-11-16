# Third-Party Documentation Index

This directory documents external components integrated or proposed for Wicofe.

## Architecture and policy
- [Third-party intake and compliance architecture 0.1](THIRD_PARTY_INTAKE_ARCHITECTURE_0.1.md) — draft process for source provenance, license review, dependency inventory, security assessment, approval scope and SBOM integration.
- [Component record template](../COMPONENT_RECORD_TEMPLATE.md) — human-readable intake record for an individual dependency.

## Scope
- Component inventory and exact upstream provenance.
- Versions, commits, source integrity, and download records.
- License texts, notices, attribution, and redistribution obligations.
- Local patch tracking, security advisories, and maintenance status.
- Dependency and enabled-feature audits.
- SBOM and release inventory reconciliation.

## Ownership
This repository owns compliance/provenance records and third-party intake policy. [Wicofe-Ports](https://github.com/Waizusora/Wicofe-Ports) owns build recipes and integration patches. Component repositories own their use of dependencies and must link to the corresponding third-party record. [Wicofe-Build](https://github.com/Waizusora/Wicofe-Build) records build provenance; [Wicofe-Image](https://github.com/Waizusora/Wicofe-Image) assembles the final image inventory.

## Approval
A successful build or an OSI-approved license alone is not sufficient approval. Review exact versions, transitive dependencies, optional features, generated code, usage context, and redistribution obligations. Approval applies only to the reviewed version/configuration/distribution context. Third-party code retains upstream licensing.

- [Central documentation index](https://github.com/Waizusora/Wicofe-Docs/blob/main/INDEX.md)
- [Repository documentation map](https://github.com/Waizusora/Wicofe-Docs/blob/main/REPOSITORY_DOCUMENTATION_MAP.md)
