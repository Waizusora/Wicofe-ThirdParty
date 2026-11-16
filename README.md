# Wicofe-ThirdParty

Third-party component inventory, integration records, patches, and license/provenance compliance for Wicofe OS.

## Scope
- Imported and externally maintained component inventory.
- Upstream source, version, commit, and download provenance.
- License texts, notices, attribution, and redistribution obligations.
- Wicofe-specific patch tracking and upstream submission status.
- Security advisories and maintenance status.
- Dependency inventories and release SBOM reconciliation.

## Dependency license policy

The authoritative [Wicofe Dependency License Policy 0.2](policies/DEPENDENCY_LICENSE_POLICY_0.2.md) applies to all direct and transitive dependencies and shipped assets:

- **GPL:** prohibited.
- **AGPL:** prohibited.
- **LGPL:** conditionally allowed after exact-version technical/license review and scoped approval; prefer in-house implementation when reasonably feasible.
- **Other licenses:** allowed when their exact terms, compatibility and obligations are reviewed and met. This includes common licenses such as MIT, BSD, ISC, Apache-2.0, MPL-2.0 and Zlib.
- **Other copyleft, custom, proprietary or ambiguous terms:** require careful compatibility review and explicit project-owner approval.
- **Unknown or incomplete license evidence:** blocked pending review.

Original Wicofe-authored code targets MPL-2.0 unless a repository explicitly documents otherwise. Third-party code retains its own license and notices; do not relicense imported code or remove notices.

## Required component record

Each imported component should record upstream name and canonical URL, exact version/tag/commit, source integrity, license text and SPDX evidence, notices, direct/transitive dependencies, enabled features, local patches, security/maintenance status, consuming repositories and approval scope.

## Suggested structure
- `components/` — one record per component.
- `patches/` — Wicofe-maintained patch series.
- `licenses/` — required license texts and notices.
- `policies/` — review and approval policy.
- `AUDIT.md` — current inventory and audit status.

## Status

Initial repository baseline. This repository does not imply that any third-party component has been approved or integrated.

## License

Original Wicofe-authored material is intended to use MPL-2.0. Third-party code and license texts remain under their respective terms.

## Component intake

Use [COMPONENT_RECORD_TEMPLATE.md](COMPONENT_RECORD_TEMPLATE.md), [third-party intake architecture](docs/THIRD_PARTY_INTAKE_ARCHITECTURE_0.1.md), and the binding [dependency license policy](policies/DEPENDENCY_LICENSE_POLICY_0.2.md).

## Automated dependency audit

The initial [Dependency License Auditor](https://github.com/Waizusora/Wicofe-Tools/blob/main/docs/DEPENDENCY_LICENSE_AUDITOR.md) is maintained in Wicofe-Tools. Its cross-repository workflow checks the canonical 29-repository set and publishes JSON/Markdown evidence artifacts. Current resolver coverage is incomplete: Cargo metadata is resolved; non-Cargo ecosystems and final-image/asset inventories remain blocked pending implementation and review. No repository-wide compliance claim is made.

## Documentation

See [docs/INDEX.md](docs/INDEX.md). The [central repository documentation map](https://github.com/Waizusora/Wicofe-Docs/blob/main/REPOSITORY_DOCUMENTATION_MAP.md) identifies canonical ownership and cross-repository boundaries.
