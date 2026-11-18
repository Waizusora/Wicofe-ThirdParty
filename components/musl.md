# musl — proposed Wlibc source foundation

## Identity

- Component: musl C library
- Upstream URL: https://git.musl-libc.org/cgit/musl/
- Integration owner: Wlibc
- Consuming repository: https://github.com/Waizusora/WLibc
- Purpose in Wicofe: Initial implementation foundation for the ISO C and POSIX C runtime, subject to native Wicofe porting.

## Source provenance

- Upstream version/tag: Not selected
- Exact source commit: Not selected
- Source archive URL: Not selected
- Archive checksum and algorithm: Not recorded
- Date retrieved: Not imported

## Licensing

- Project-level SPDX license identifier: MIT
- License evidence: upstream COPYRIGHT file at https://git.musl-libc.org/cgit/musl/tree/COPYRIGHT
- Copyright holders: Rich Felker and musl contributors, as identified by the selected upstream revision.
- Required notices/attributions: Preserve upstream COPYRIGHT, per-file notices, and notices for bundled components.
- Third-party terms: Some source portions identify separate BSD, public-domain, or other permissive terms; audit each included component and its exact revision.
- License review status: Preliminary project-level MIT evidence found; exact-revision and file/component audit pending.

## Dependency audit

- Direct dependencies: Not audited; exact revision not selected.
- Transitive dependencies: Not audited.
- Optional features enabled: Not selected.
- Build-time tools and generators: Not audited.
- Generated or vendored files: None imported at this stage.
- License findings: No source import is approved by this preliminary record.

## Wicofe modifications

- Local patch list: None; source not imported.
- Patch rationale: Pending native Wicofe syscall ABI port.
- Target architectures: Wicofe initial targets x86-64 and AArch64, subject to upstream source and port review.

## Security and maintenance

- Upstream maintenance status: Must be checked at the time an exact revision is selected.
- Known advisories reviewed: Not yet reviewed for a pinned revision.
- Update/removal plan: Track upstream releases and security advisories; maintain a reviewed patch series.

## Decision

- Status: Proposed — NOT APPROVED FOR IMPORT
- Decision record: Wlibc licensing and provenance policy.
- Approval gate: Pin exact commit and archive hash; preserve upstream COPYRIGHT; review every included third-party component, generated file, and enabled optional feature; complete security and build review; obtain explicit approval.
