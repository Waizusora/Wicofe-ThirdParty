# musl — pinned Wlibc source foundation

## Identity

- Component: musl C library
- Upstream URL: https://git.musl-libc.org/git/musl
- Integration owner: Wlibc
- Consuming repository: https://github.com/Waizusora/WLibc
- Purpose in Wicofe: Initial source foundation for the ISO C17 and POSIX.1-2024 C runtime, subject to native Wicofe porting.

## Pinned source provenance

- Version file: 1.2.6
- Ref: master snapshot
- Exact commit: 7813e9119eb5fe681b6750b8a033a0490bca0941
- Tree: dc8444f8e5dfcc3a592dd62653d17a61f8d773a1
- Committer date: 2026-10-14T22:48:56Z
- Mirror last refreshed: 2026-11-17
- Source archive URL: not downloaded
- Archive checksum: not recorded
- Wlibc lock: https://github.com/Waizusora/WLibc/blob/main/upstream/musl.lock
- Baseline review: https://github.com/Waizusora/WLibc/blob/main/docs/UPSTREAM_BASELINE_MUSL_1.2.6.md

The selected commit is pinned for audit, not approved as an imported source snapshot. Re-check the official upstream ref and compute the source archive hash before importing.

## Licensing

- Project-level SPDX license identifier: MIT
- License evidence: exact upstream COPYRIGHT file preserved at https://github.com/Waizusora/WLibc/blob/main/licenses/musl/COPYRIGHT
- Copyright holders: preserve all holders and contributors listed by the selected upstream revision.
- Required notices: retain upstream COPYRIGHT, per-file notices, and all bundled third-party license terms.
- Identified third-party portions include TRE regex (2-clause BSD), separately attributed math routines, optimized memory routines, DES (BSD), Blowfish (public domain with fallback permissive terms), and smoothsort (MIT-style). See the pinned COPYRIGHT for details.
- Review status: project-level MIT confirmed; complete file/component audit pending.

## Dependency audit

- Exact source tree: 2,897 entries.
- Wicofe initial architecture targets: x86_64 and aarch64.
- Other upstream architecture ports are outside the initial Wicofe target.
- Build-time tools, generated files, selected source closure and optional components: not yet audited file-by-file.
- License findings: first-pass only; import is not approved.

## Wicofe modifications

- Local patch list: none; source not imported.
- Native syscall port: blocked on Wicofe-ABI draft.
- GNU/BSD public compatibility extensions: out of scope.
- POSIX interfaces: retain/implement according to Wlibc POSIX.1-2024 conformance matrix; do not remove internal helpers without dependency analysis.

## Security and maintenance

- Review upstream security advisories and relevant mailing-list notices when importing and before each update.
- Keep upstream import and Wicofe-specific patches in separate commits.
- Maintain a reproducible source archive hash and source-to-binary provenance.

## Decision

- Status: PINNED FOR AUDIT — NOT YET IMPORTED OR APPROVED FOR BUILD.
- Exact revision selected: yes.
- Root license confirmed: yes, MIT.
- Detailed third-party audit: pending.
- Source archive hash: pending.
- Native Wicofe port: blocked by ABI specification.
