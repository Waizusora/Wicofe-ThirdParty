# Wicofe Third-Party Dependency License Policy 0.2

**Identifier:** WIC-GOV-LICENSE-001  
**Version:** 0.2.0  
**Status:** Project policy — approved by project owner  
**Owner:** Wicofe project; compliance records owned by Wicofe-ThirdParty  
**Applies to:** All Wicofe repositories, direct/transitive dependencies, build tools, SDKs, ports, images, installers, updates, recovery media, firmware, fonts, codecs, schemas, generated assets and shipped dependencies  
**Effective date:** 2026-11-16

## 1. Purpose

Wicofe is intended to be an independent alternative. Original implementation is preferred where it is technically and economically reasonable, but external dependencies are allowed when their license and obligations are compatible with this policy. Dependency adoption must consider long-term maintenance, security, portability, supply-chain risk and the cost of an in-house implementation.

## 2. License decisions

### 2.1 GPL — prohibited

Software and assets licensed under any GNU General Public License version (including GPL-2.0 and GPL-3.0, with or without the “or later” option) MUST NOT be introduced as direct or transitive dependencies, vendored source, linked libraries, plugins, runtime components, build-time dependencies required for Wicofe products, or other incorporated components.

### 2.2 AGPL — prohibited

Software and assets licensed under any GNU Affero General Public License version (including AGPL-3.0) MUST NOT be introduced as dependencies or shipped components. Network interaction does not create an exception.

### 2.3 LGPL — conditionally allowed

LGPL components may be considered only when no technically and legally suitable permissively licensed alternative is available. First evaluate permissive alternatives and the feasibility of a maintainable in-house implementation. If a from-scratch implementation would be disproportionately difficult, risky, or wasteful, an upstream LGPL component may be considered only after scoped technical and license review and explicit project-owner approval. This is an exception path, not a preferred dependency choice.

Mandatory conditions:
1. Identify the exact component, version, source commit, LGPL version, files, enabled features, integration method, target and distribution model.
2. Document why the functionality is needed and why an in-house implementation is not reasonably feasible, or why using the upstream implementation is materially safer/more maintainable.
3. Inspect the full transitive dependency closure and all license exceptions or dual-license terms.
4. Prefer a replaceable shared-library boundary where technically suitable.
5. For static linking, verify the applicable relinking requirements and provide all materials required by the exact license.
6. Preserve source availability, notices, modification notices and installation/relinking information as required by the exact license and distribution model.
7. Keep LGPL-covered source clearly separated; do not relicense upstream files as Wicofe code.
8. Review the consequences for kernel, boot chain, privileged boundaries, SDK, image and recovery distributions. Avoid placing LGPL code in critical trust boundaries unless specifically justified and approved.
9. Record security, maintenance, ABI compatibility, architecture support, update and replacement tests.
10. Obtain Wicofe-ThirdParty review and explicit project-owner approval before release distribution.

LGPL-2.1, LGPL-3.0 and exception-bearing variants are not interchangeable. Failure to satisfy applicable obligations blocks adoption/distribution.

### 2.4 Permissive licenses — preferred subject to review

Wicofe prefers permissive licenses such as MIT, BSD variants, ISC, Apache-2.0 and Zlib when their exact terms are suitable. Dependencies under these licenses are still subject to exact-license review and compliance with all applicable terms. Other non-GPL/AGPL licenses, including MPL-2.0 and other copyleft licenses, require compatibility review and explicit project-owner approval where applicable.

Approval is not automatic. For every component, review:
- Exact license identifier/version and complete license text.
- Copyright, attribution and NOTICE requirements.
- Patent grants, patent termination clauses and trademark restrictions.
- Source-distribution, modification and binary redistribution requirements.
- File-level copyleft or reciprocal obligations.
- Dual licensing, exceptions, additional terms and bundled assets.
- Compatibility with the license of the Wicofe component that incorporates it and the intended distribution model.

Permissive licenses may usually be simpler to integrate, but required notices and conditions must still be met. MPL-2.0 file-level obligations must be respected. Other copyleft licenses that are not GPL/AGPL are not categorically prohibited by this policy, but require a careful compatibility review and explicit project-owner approval before integration into distributed products. No license may be assumed compatible merely because it is open source.

### 2.5 Unknown, custom and proprietary terms

Unknown, missing, ambiguous, custom, source-available or proprietary terms require manual review before use. They are not automatically accepted. The project owner must approve the exact use and distribution obligations in writing. If rights to use, modify, build or redistribute the component are unclear, block adoption until clarified.

## 3. In-house implementation preference

Before adding a dependency, document:
- The concrete requirement and criticality.
- Whether the feature can be deferred, omitted or simplified.
- Whether a suitable permissively licensed upstream component exists.
- Whether Wicofe can implement it with existing code and reasonable engineering effort.
- Whether a from-scratch implementation would be disproportionately difficult, risky, or wasteful.
- Expected security, maintenance, performance and portability impact of reuse versus an in-house implementation.
- Available alternatives and why the selected option is preferable.
- How coupling can be minimized and future replacement preserved.

Independent implementation is encouraged where practical, but Wicofe does not require difficult components to be recreated from scratch. Reuse or fork a suitable upstream project when that is the safer and more maintainable engineering choice, provided its license and architecture satisfy this policy. Convenience alone is not sufficient justification for choosing a copyleft dependency when a suitable permissive alternative exists.

## 4. Approval workflow

1. **Proposed:** not yet approved for release artifacts.
2. **Evidence collection:** exact source, version, hashes, license texts, notices, dependency tree and asset inventory.
3. **Technical review:** need, in-house feasibility, alternatives, security, maintenance and integration boundary.
4. **License review:** exact license/version, combination and distribution obligations.
5. **Project approval:** record a scoped decision in Wicofe-ThirdParty. GPL/AGPL proposals are rejected; LGPL needs explicit approval; other licenses are assessed under §2.4.
6. **Integration:** pin immutable source, preserve notices, record patches, produce SBOM and add tests.
7. **Release gate:** reconcile build and image inventories and include all required compliance materials.
8. **Re-review:** triggered by version, feature, license, linking, target, packaging or distribution changes.

No dependency becomes approved solely because it builds, passes CI or is already used upstream.

## 5. Transitive and non-code dependencies

The policy applies to the complete dependency closure: build tools, compiler plugins, proc macros, code generators, vendored files, firmware, fonts, codecs, schemas, test data, generated code and runtime-loaded modules. A prohibited GPL/AGPL component anywhere in the required dependency closure blocks adoption. The license of generated output must be assessed based on its source inputs and generation process.

## 6. Enforcement

- Identify exact licenses for direct and transitive dependencies.
- Reject GPL and AGPL immediately.
- Permit other licenses only after obligations and compatibility are reviewed.
- Require explicit scoped approval for LGPL and non-GPL/AGPL copyleft, custom or proprietary terms.
- Treat unknown or incomplete license evidence as blocked pending review.
- Preserve evidence and notices; never auto-relicense or delete upstream license files.
- Automated tools may detect and block policy violations but cannot grant legal approval.
- Release engineering MUST fail closed when inventory is incomplete or a prohibited/unapproved component is present.

## 7. Required dependency record

Record component/version/commit, hashes, license evidence, dependency closure, affected repositories, enabled features, integration/linking details, notices, patches, reviewer, project-owner approval where required, conditions, review trigger, security assessment, SBOM identifiers, tests and removal/replacement plan.

## 8. Authority and amendment

Only the Wicofe project owner may approve exceptions or amend this policy. Record rationale, scope, affected repositories and effective date. Silence, historical use, successful CI or upstream popularity is not approval.

## 9. Compliance status

This policy does not prove existing repositories or release images comply. Dependency manifests, vendored source, build outputs and release images must be inventoried and checked against it.

**Summary:** Avoid GPL and AGPL; they are prohibited for normal project integration. Prefer suitable permissive licenses. LGPL may be considered only when no suitable permissive alternative exists and after exact review and explicit approval. Reuse or fork existing components when implementing them from scratch would be disproportionately difficult or would materially worsen security or maintainability.
