# Wicofe Third-Party Intake and Compliance Architecture 0.1

**Status:** Draft policy and data model. This document defines intake, provenance and review controls. It does not approve any dependency or establish legal compatibility for a specific component.

## 1. Purpose

Wicofe-ThirdParty is the canonical record for externally sourced components used or proposed across Wicofe repositories. It provides traceable source provenance, exact version identity, license/notice obligations, dependency inventory, patch history, security status and review decisions.

A component being open source, widely used, or successfully compiled does not by itself make it approved for Wicofe.

## 2. Ownership boundaries

| Repository | Canonical responsibility |
|---|---|
| Wicofe-ThirdParty | Third-party intake policy, provenance records, license/notice inventory, compliance review and audit status |
| Wicofe-Ports | Build recipes, integration patches and port maintenance |
| Wicofe-Build | Whole-system dependency graph, build orchestration and artifact provenance |
| Wicofe-SDK | SDK-bundled toolchain inventory and distribution notices |
| Component repositories | Dependency selection, feature configuration and use within the component |
| Wicofe-Image | Per-image component inventory and release license bundle |
| Wicofe-Tests | Automated policy and supply-chain validation suites |

This repository records and reviews dependencies; it does not own their source code, build integration, or component-local dependency declarations. Each consuming repository remains responsible for declaring its actual dependency use and linking to the canonical record.

## 3. Component identity and source provenance

A component record must identify the exact upstream project and source artifact:
- canonical upstream project URL and maintainer;
- exact release/version and immutable source commit;
- source archive or repository reference;
- retrieval date and source origin;
- cryptographic digest and algorithm for downloaded archives;
- signed release/tag verification result, if available;
- local mirror/cache identity, if used;
- submodules, vendored code and generated source provenance.

Do not identify source solely by a branch name, mutable URL, package name or version string. If upstream does not publish a signed release, record that limitation and the independent verification method. A checksum proves byte identity against a known digest, not that the upstream author is trustworthy.

## 4. License and notice review

Record exact license evidence, not only a guessed SPDX identifier:
- SPDX license expression, where determinable;
- license files and their paths/hashes;
- copyright holders and relevant years;
- required attribution and notice files;
- source-distribution, modification and offer obligations;
- patent, trademark and export clauses where applicable;
- linking, static/dynamic combination and plugin considerations;
- documentation, fonts, firmware, test data and generated assets;
- reviewer, review date, decision and rationale.

Use SPDX identifiers and expressions where applicable, but retain the actual license texts and notices. NOASSERTION or LicenseRef identifiers may be necessary when the license cannot be mapped confidently. Do not infer a license from a repository badge or package registry metadata alone.

MPL-2.0 is the intended license for original Wicofe-authored code. It does not automatically relicense third-party code or establish that every dependency is compatible with every distribution model. GPL-family, LGPL, AGPL, proprietary, dual-licensed and exception-bearing components require exact license/version and combination review. Do not blanket-approve or blanket-reject a family without analyzing the actual terms and planned use.

## 5. Dependency graph and feature audit

A component's record must enumerate:
- direct runtime dependencies;
- transitive runtime dependencies;
- build-time tools and compiler plugins;
- optional features enabled and disabled;
- bundled/vendored libraries;
- generated code and code generators;
- target-specific dependencies and conditional compilation;
- dynamically loaded modules/plugins;
- firmware, fonts, codecs, schemas, test fixtures and other non-code assets.

The audit must reflect the actual build configuration shipped by Wicofe, not every theoretical upstream feature. Record how the inventory was generated and its limitations. A dependency manifest or SBOM is evidence to review, not an automatic legal approval.

## 6. Patch and integration tracking

For every local modification, record:
- patch filename or immutable patch commit;
- affected upstream version and source files;
- reason for the patch;
- security or behavior impact;
- whether submitted upstream and its review status;
- whether the patch changes licensing, notices or generated artifacts;
- build configuration and target architectures affected.

Prefer small, reviewable patch series. Do not edit vendored upstream code without recording the patch and retaining license notices. When updating upstream, re-run provenance, license, feature and vulnerability review for the new exact source.

## 7. Security and maintenance assessment

Track:
- upstream maintenance and release cadence;
- supported branches and end-of-life status;
- vulnerability disclosure channel;
- advisories reviewed and affected version ranges;
- known vulnerabilities and mitigation status;
- patch availability and local backport status;
- risk owner and planned update/removal date.

Security status is time-sensitive. Store an audit timestamp and evidence links. An old clean audit must not be presented as proof that a component remains vulnerability-free.

## 8. Review workflow and status model

Suggested states:
1. **Proposed:** identified but not yet fully reviewed.
2. **Under review:** source, license, feature or security review is in progress.
3. **Approved:** exact version, configuration, usage context and distribution obligations have been reviewed and accepted by the designated maintainers.
4. **Conditionally approved:** accepted only with explicit constraints, such as disabled features, patch requirements, limited distribution or additional notices.
5. **Rejected:** not approved for the stated use; record reason.
6. **Deprecated:** retained temporarily but no longer recommended for new integration.
7. **Removed:** no longer shipped or used; retain historical provenance and removal evidence.

Approval is scoped to a precise version, feature set, integration method and distribution context. A new version, enabled feature, changed linking model or changed distribution channel requires reassessment. Conditional approval must name an owner and measurable conditions; it must not be treated as unconditional approval.

## 9. Component record schema

The repository's COMPONENT_RECORD_TEMPLATE.md is the human-readable intake template. A future machine-readable schema should include stable component ID, upstream identity, immutable source reference, artifact hashes, license evidence, dependency inventory, feature configuration, patch set, security review, consuming repositories, approval scope, reviewer and timestamps.

Machine-readable records must be versioned and validated. Unknown required fields, invalid status transitions, missing source identity, missing review scope and missing license evidence must block approval.

## 10. SBOM and release integration

Produce a software bill of materials for each relevant release artifact and complete image. The SBOM should identify component versions, relationships, package identifiers, licenses where known, source provenance and generation tool/version.

Keep these records distinct:
- source repository inventory;
- build-time dependency inventory;
- target runtime dependency inventory;
- SDK/toolchain inventory;
- final image inventory.

A component may be present in a build environment but absent from the shipped image; likewise a firmware or data asset may ship without being a conventional package dependency. Record the scope of each SBOM and its known blind spots.

Wicofe-Build should attach source/toolchain provenance to build outputs. Wicofe-Image should assemble the final selected-component inventory and license notices. Wicofe-ThirdParty provides the canonical reviewed component records those manifests reference.

## 11. Automation and audit

Automated checks may validate:
- required component record fields;
- immutable version/commit references;
- source archive digest presence;
- license file and SPDX expression syntax;
- declared direct/transitive dependency inventory;
- patch references and upstream version consistency;
- consuming repository links;
- stale security review timestamps;
- approval status and scoped conditions;
- SBOM consistency between build and image manifests.

Automation may flag missing evidence but must not make nuanced legal compatibility decisions without designated human review. Do not mark an audit complete merely because a scanner returned no findings.

## 12. Security of intake

Treat source archives, Git submodules, build scripts, package metadata and generated code as untrusted. Verify archive paths and symlinks before extraction, pin retrieval to immutable references, isolate build execution, and avoid granting dependency build scripts unnecessary host privileges or credentials.

Keep credentials and private signing keys out of component records and public logs. Record hashes and public provenance metadata instead.

## 13. Licensing policy

Original Wicofe-ThirdParty code targets MPL-2.0. Third-party license texts and notices remain under their respective terms. Do not remove, alter or relicense upstream notices. Distribution review must consider source obligations, notices, binary redistribution, modifications, linking/combination and all shipped assets.

This architecture is a process framework, not legal advice. Ambiguous or high-impact licensing cases require review by an appropriately qualified reviewer before distribution.

## 14. Testing requirements

- Record schema validation and required-field tests.
- Immutable source/version and checksum verification.
- Archive extraction traversal and symlink security tests.
- SPDX expression parser and license-file presence checks.
- Dependency graph completeness and cycle detection.
- Feature configuration and generated/vendor source inventory checks.
- Patch applicability and upstream revision consistency.
- Approval scope and status transition tests.
- Stale security review and advisory workflow checks.
- SBOM generation, parsing and build/image reconciliation.
- Negative fixtures for missing, ambiguous and conflicting license evidence.

## 15. Open decisions

- Human-readable record versus canonical machine-readable schema.
- SPDX document profile and SBOM format/version.
- Approved license-review roles and escalation path.
- Review cadence and stale-record thresholds.
- Source mirror and archive retention policy.
- Signature verification requirements by upstream ecosystem.
- Security advisory data sources and triage SLA.
- Policy for proprietary firmware, fonts, codecs and data assets.
- Criteria for conditional approval and exception expiry.
- Release artifact attestation and signing integration.

## 16. Completion criteria

A dependency may be marked approved only for a documented exact source version, feature set, integration and distribution context, with verified provenance, reviewed license/notice obligations, dependency inventory, patch record, security assessment and named reviewer. Repository-wide compliance requires reconciliation against actual build outputs and final images. Until those records and checks exist, this remains a draft architecture and no component is implicitly approved.
