# Wicofe Third-Party Dependency License Policy 0.1

**Identifier:** WIC-GOV-LICENSE-001  
**Version:** 0.1.0  
**Status:** Project policy — approved by project owner  
**Owner:** Wicofe project; compliance records owned by Wicofe-ThirdParty  
**Applies to:** All Wicofe repositories, build tools, SDKs, ports, images, installers, updates, recovery media, firmware, fonts, codecs, schemas, generated assets and shipped dependencies  
**Effective date:** 2026-11-16

## 1. Purpose

Wicofe is intended to be an independent alternative. Original implementation is the default. A third-party dependency is an exception and requires evidence that the capability is essential and cannot reasonably be implemented in-house within acceptable technical, security, maintenance and schedule constraints.

## 2. License decisions

### 2.1 GPL — prohibited

GPL-licensed code or assets MUST NOT be introduced as direct or transitive dependencies, vendored source, linked libraries, plugins, runtime components, build-time dependencies shipped as part of a Wicofe product, or other incorporated components. No ordinary project exception is permitted.

### 2.2 AGPL — prohibited

AGPL-licensed code or assets MUST NOT be introduced in any dependency or shipped component. Network interaction does not create an exception. No ordinary project exception is permitted.

### 2.3 LGPL — conditionally permitted

LGPL is the only third-party software license family eligible for a project-level dependency exception. It is never pre-approved. Approval applies only to the exact component, version, LGPL version, files, enabled features, integration method, target and distribution model.

All conditions below are mandatory:

1. The capability is essential to Wicofe and cannot reasonably be implemented in-house.
2. The component owner documents the requirement, feasibility analysis, alternatives considered and why no suitable Wicofe-owned or non-LGPL option is viable.
3. Wicofe-ThirdParty verifies exact license texts, SPDX expression, notices, exceptions, source provenance, transitive dependencies and bundled/generated assets.
4. A qualified license reviewer assesses the exact LGPL version and combination. LGPL-2.1, LGPL-3.0 and exception-bearing variants are not interchangeable.
5. Prefer a separately replaceable shared-library boundary. Static linking is prohibited unless all required relinkable object files are supplied and every applicable relinking and notice obligation is met.
6. Users must retain the practical ability to replace or modify the LGPL component and use the modified component with the Wicofe application to the extent required by the applicable LGPL version.
7. Required source code, modification notices, license texts, copyright notices, relinking materials and installation information (where applicable) MUST be supplied in the required form.
8. Keep LGPL-covered source files separate from original Wicofe files. Never copy LGPL implementation into Wicofe-owned MPL-2.0 files or claim upstream code is relicensed.
9. Do not place LGPL dependencies in the kernel, boot-critical trust chain, privileged security boundary or recovery trust root unless the project owner and qualified reviewer explicitly approve the exact architecture and obligations. Default: avoid such placement.
10. Security, update, ABI compatibility, architecture support, replacement testing, notices and SBOM coverage are mandatory approval/release checks.
11. Every approval has a named owner, review date, expiry/review trigger and removal plan. A version, feature, linking, target or distribution change requires re-review.

Failure of any condition means the dependency is not approved.

### 2.4 All other third-party dependency licenses — not permitted

Third-party software under licenses other than LGPL is not eligible for normal dependency approval. This includes permissive, public-domain-dedication, copyleft, proprietary, source-available and custom licenses. Do not assume a permissive license is automatically acceptable.

An exception outside LGPL requires a separate, explicit policy amendment by the project owner before adoption. A maintainer, component owner, build script or automated scanner cannot grant such an exception.

### 2.5 Original Wicofe work

Original Wicofe-authored code targets MPL-2.0, subject to the repository's explicit license file and any separately documented project decision. This does not relicense upstream material. Keep third-party code, notices and provenance separate.

## 3. Essentiality and in-house feasibility

Every proposed LGPL dependency must document:
- Concrete system requirement and why it is critical.
- Whether the feature can be omitted, simplified or deferred.
- Whether Wicofe can implement it using existing project-owned code.
- Engineering effort, expertise, security and maintenance burden of an in-house implementation.
- Alternatives evaluated and why they fail the requirement.
- Consequences of not including the dependency.
- A strategy to reduce coupling and retain a replacement path.

“Faster”, “popular”, “already used elsewhere”, “convenient” or “avoids writing code” are not sufficient reasons.

## 4. Approval workflow

1. **Proposed:** no use in release artifacts.
2. **Evidence collection:** exact source, version, hashes, license texts, dependency tree and asset inventory.
3. **Technical review:** essentiality, in-house feasibility, alternatives, security, maintenance and integration boundary.
4. **License review:** exact LGPL version and distribution obligations reviewed by a qualified reviewer.
5. **Project approval:** project owner records a scoped decision in Wicofe-ThirdParty.
6. **Integration:** pin immutable source, preserve notices, record patches, produce SBOM and add replacement/compliance tests.
7. **Release gate:** build and image inventories reconciled; all required materials included.
8. **Re-review:** triggered by relevant version, feature, target, linking, packaging or distribution changes.

No dependency may become Approved or Conditionally Approved before all mandatory evidence and approvals exist.

## 5. Transitive and non-code dependencies

The policy applies to the complete dependency closure, not only direct package declarations. Review build-time tools, compiler plugins, code generators, vendored files, firmware, fonts, codecs, schemas, test data, generated code and runtime-loaded modules.

A prohibited license anywhere in the shipped or required dependency closure blocks adoption. An LGPL transitive dependency must satisfy the same conditions as a direct dependency.

## 6. Enforcement

- Default-deny unknown, missing, ambiguous or unreviewed licenses.
- Reject GPL and AGPL immediately.
- Reject all third-party dependency license families other than LGPL unless this policy is formally amended.
- Treat LGPL as blocked until scoped approval exists.
- Scan manifests, lockfiles, vendored source, build tools and final image/SBOM inventories.
- Preserve evidence and notices; never auto-relicense or delete upstream license files.
- Automated tooling may block violations but cannot grant legal approval.
- Release engineering MUST fail closed when dependency inventory is incomplete or a prohibited/unapproved component is present.

## 7. Required record for each approved LGPL dependency

The canonical Wicofe-ThirdParty record must include exact component/version/commit, hashes, license evidence, dependency closure, affected repositories, enabled features, static/dynamic integration details, source and relink delivery plan, notices, reviewer, project-owner approval, conditions, expiry/review trigger, security assessment, SBOM identifiers, tests and removal plan.

## 8. Authority and amendment

Only the Wicofe project owner may approve an exception or amend this policy. Any amendment must record rationale, scope, affected repositories and effective date. Silence, historical use, successful CI or upstream popularity is not approval.

## 9. Compliance status

This policy becomes operational only after repository dependency manifests, vendored source, build outputs and release images are inventoried and checked. Until then, existing dependencies are **not yet verified**, not presumed compliant.

**Summary:** GPL prohibited. AGPL prohibited. LGPL conditionally allowed only when essential, not reasonably implementable in-house, technically isolated where possible, legally reviewed and explicitly approved. All other third-party dependency licenses are disallowed unless this policy is formally amended.
