# Wicofe-ThirdParty

Third-party component inventory, integration records, patches, and license/provenance compliance for Wicofe OS.

## Scope

- Inventory of imported and externally maintained components.
- Upstream source, version, commit, and download provenance records.
- License texts, notices, attribution, and redistribution obligations.
- Wicofe-specific patch tracking and upstream submission status.
- Security advisories and maintenance status for integrated components.
- Build and integration notes for approved third-party software.
- Dependency inventories and release SBOM reconciliation.

## Dependency license policy

The authoritative [Wicofe dependency license policy](policies/DEPENDENCY_LICENSE_POLICY_0.1.md) applies to every direct and transitive dependency and shipped asset:

- GPL: prohibited.
- AGPL: prohibited.
- LGPL: conditionally allowed only when essential, not reasonably implementable in-house, isolated where practical, legally reviewed and explicitly approved by the project owner.
- All other third-party dependency licenses: not permitted unless the policy is formally amended.
- Unknown or incomplete license evidence: blocked.

Original Wicofe-authored code targets MPL-2.0. Third-party code retains its own license and notices; do not relicense imported code or remove notices.

## Required component record

Each imported component should have a record containing:

- Upstream name and canonical URL.
- Exact version, release tag, and source commit.
- License identifier and included license/notice files.
- Download/source provenance and integrity information where available.
- Local patches and rationale.
- Build configuration and enabled optional features.
- Direct and transitive dependency/license review.
- Security and maintenance status.
- Wicofe integration owner and approval status.

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

Use [COMPONENT_RECORD_TEMPLATE.md](COMPONENT_RECORD_TEMPLATE.md) to record source provenance, exact versions, license obligations, enabled features, patches, and review decisions. Review the [third-party intake architecture](docs/THIRD_PARTY_INTAKE_ARCHITECTURE_0.1.md) and the binding [dependency license policy](policies/DEPENDENCY_LICENSE_POLICY_0.1.md).

## Documentation

See [docs/INDEX.md](docs/INDEX.md) for this repository's technical documentation. The [central repository documentation map](https://github.com/Waizusora/Wicofe-Docs/blob/main/REPOSITORY_DOCUMENTATION_MAP.md) identifies canonical ownership and cross-repository boundaries.
