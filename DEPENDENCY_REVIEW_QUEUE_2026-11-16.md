# Wicofe Dependency License Review Queue — 2026-11-16

**Policy:** [Dependency License Policy 0.2](policies/DEPENDENCY_LICENSE_POLICY_0.2.md)  
**Evidence run:** [Wicofe-Tools cross-repository audit 43878335380](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43878335380)  
**Machine-readable per-repository reports:** [Audit artifact 14231212277](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43878335380/artifacts/14231212277)  
**Overall result:** BLOCKED. This queue is evidence triage, not legal approval.

## 1. Status summary

| Status | Records | Decision |
|---|---:|---|
| REJECTED | 2 | GPL host tools; replace before release |
| NEEDS_REVIEW | 244 | No scoped decision recorded |
| UNKNOWN | 101 | Source/license identity or evidence incomplete |
| PASS / APPROVED_WITH_CONDITIONS | 0 | No approved dependency records in this audit snapshot |
| **Total** | **347** | **BLOCKED** |

The 347 records include Cargo packages, GitHub Actions, build commands, system packages, runner images, toolchains and downloaded artifacts. They are not all Cargo packages.

## 2. Replacement queue — prohibited GPL

Both records are from Wicofe-Kernel's CI workflow and are build/test host dependencies, not files shipped in the ISO. Policy 0.2 has no build-only exception.

| Component | Version | Current role | License | Required action |
|---|---|---|---|---|
| `qemu-system-x86` | `1:10.2.1+ds-1ubuntu3.3` | x86-64 BIOS boot validation | GPL-2.0-or-later | Replace with a permitted emulator and prove boot-log parity |
| `xorriso` | `1:1.5.6-1.1ubuntu4` | ISO generation and ISO notice inspection | GPL-2.0-or-later | Replace with a permitted ISO authoring/inspection tool and prove ISO/El Torito parity |

Candidates under technical/license review:
- QEMU: [Bochs 3.1](https://github.com/bochs-emu/Bochs/tree/REL_3_1_FINAL), source snapshot `30cfd566ecc8deb33e56e801e32b444a7041b6d2`, upstream [LGPL-2.1 LICENSE](https://github.com/bochs-emu/Bochs/blob/30cfd566ecc8deb33e56e801e32b444a7041b6d2/LICENSE). Its upstream README confirms x86-64 PC/BIOS emulation. It is a plausible replacement for the current x86-64 BIOS test, but its file-level license notices, package closure, serial logging, performance and boot-marker parity must be checked. It is not an AArch64 emulator.
- xorriso: [PyCdlib 1.22.0](https://pypi.org/project/pycdlib/), source snapshot `fbf3079c6254054a1da03fccb1f84763f5f20b28`, upstream [LGPL-2.1-only COPYING](https://github.com/clalancette/pycdlib/blob/fbf3079c6254054a1da03fccb1f84763f5f20b28/COPYING). Upstream documentation demonstrates El Torito bootable ISO creation. It may replace the xorriso ISO-authoring call through its Python API, but requires explicit LGPL approval and exact BIOS boot-info-table, Rock Ridge/Joliet, file ordering, volume metadata, and byte/boot parity tests. Its upstream packaging test recipe references genisoimage; do not import that GPL test dependency into Wicofe CI.
- xorriso: cdrtools/mkisofs (CDDL-1.0; explicit other-copyleft review/approval required) or libisofs/libburn (LGPL-family; linking/relinking and notice review required).

No candidate is approved. All require exact source/license and dependency-closure review before integration.

No candidate is approved. Do not remove either current tool until a replacement has been built, exercised and compared against the existing ISO/boot validation behavior.

## 3. LGPL-bearing optional license alternatives

The WDE all-target Cargo metadata includes two `r-efi` package versions with this exact Cargo license expression:

`MIT OR Apache-2.0 OR LGPL-2.1-or-later`

| Package | Version | SHA-256 checksum | Required by | Target condition |
|---|---|---|---|---|
| `r-efi` | 5.3.0 | `69cdb34c158ceb288df11e18b4bd39de994f6657d83847bdffdbd7f346754b0f` | `getrandom 0.3.4` | `target_os = "uefi" && getrandom_backend = "efi_rng"` |
| `r-efi` | 6.0.0 | `f8dcc9c7d52a811697d2151c701e0d08956f92b0e24136cf4cf27b57a6a0d9bf` | `getrandom 0.4.3` | `target_os = "uefi" && getrandom_backend = "efi_rng"` |

Upstream: [r-efi/r-efi](https://github.com/r-efi/r-efi).

The Cargo metadata capture intentionally retained target-conditioned dependency edges without `--filter-platform`. These two edges are UEFI-specific; they are not evidence that WDE's current Linux desktop build links an LGPL library. They remain NEEDS_REVIEW until the supported target matrix confirms whether UEFI is in scope and a human records an explicit selected license branch. MIT and Apache-2.0 are declared alternatives, but the auditor must not choose one automatically. If the LGPL branch is selected, the full LGPL-2.1 obligations and approval requirements apply.

## 4. UNKNOWN queue — 101 records, 26 unique identities

These names are not license approvals. Many are unpinned command/runner references rather than package identities; they need exact source/version/provenance and license evidence.

### Unpinned build commands and tools

- `apt-install`, `apt-update`
- `curl`, `git-clone`, `rustup-install`
- `compiler`, `dpkg-query`, `readelf`, `tar`
- `qemu-system`, `xorriso` (command-use records; the corresponding GPL system packages are separately REJECTED)
- `rust-toolchain` (multiple repositories use an unpinned toolchain command/reference)
- `rustc stable`

### Runner images

- `ubuntu-latest`
- `ubuntu-26.04`
- `${{ matrix.runner }}`

Runner labels are mutable image selectors, not immutable OS image digests. Capture actual image version and installed package deltas for each CI run.

### System packages without resolved license evidence in this artifact

- `libegl1-mesa-dev`
- `libgles2-mesa-dev`
- `libwayland-dev`
- `libx11-dev`
- `libxcursor-dev`
- `libxi-dev`
- `libxinerama-dev`
- `libxkbcommon-dev`
- `libxrandr-dev`
- `musl-tools`

Obtain exact package version, source package, copyright/license evidence and transitive system package closure from the actual CI runner. Do not infer license from the package name.

## 5. NEEDS_REVIEW queue — 244 records

The audit contains 217 Cargo records, 22 GitHub Actions records and other build-time records. All require scoped review; upstream SPDX/Cargo metadata or a license URL is evidence, not approval.

Prioritize:
1. Direct dependencies and dependencies enabled by shipped features/targets.
2. Core and security-sensitive runtime dependencies.
3. Compiler plugins, proc macros, build scripts and tools that execute during release builds.
4. External GitHub Actions and their bundled/transitive dependencies.
5. System packages, runner images and downloaded artifacts.
6. Transitive dependencies not present in the default feature set but enabled by supported target configurations.

The artifact JSON records package/version, source, checksum, license metadata, evidence, direct/transitive relationship, enabled features, dependency kind and parent edges where available. Use the exact artifact records for individual review rather than recreating the graph from names.

## 6. Approved inventory

**Zero dependencies were marked PASS or APPROVED_WITH_CONDITIONS in this snapshot.**

The example decision registry is intentionally empty. Do not populate it until the required technical and license review is completed and the authorized human decision is recorded with exact scope, reviewer, approver, evidence and conditions. For LGPL, verify source/relinking obligations, notices, distribution model, linking method and replacement capability before setting `conditions_verified`.

## 7. Non-code and release inventory gaps

- Two known vendored Limine notice/license files are recorded as UNKNOWN asset records pending full source/binary distribution reconciliation.
- No Git submodules were detected by the current scan; this does not prove the absence of vendored source or binary assets.
- Firmware, fonts, codecs, schemas, generated code, binary assets and final image contents still require inspection.
- Security and maintenance status remain NOT_ASSESSED for the dependency records in this snapshot.

## 8. Release gate

The strict audit run [43878335380](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43878335380) failed closed and uploaded artifact [14231212277](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43878335380/artifacts/14231212277). This is the correct result while rejected, unknown and unapproved records remain.

**No Wicofe-wide license-compliance claim is made.**
