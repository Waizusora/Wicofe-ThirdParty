# CI Action Dependency Inventory

**Audit date:** 2026-11-16  
**Policy:** [Wicofe Dependency License Policy 0.2](policies/DEPENDENCY_LICENSE_POLICY_0.2.md)  
**Status:** Evidence collected; all entries remain NEEDS_REVIEW until owner approval and consumer pinning are verified.

## Scope and result

The cross-repository scanner found 22 GitHub Actions dependency records across Mysh, Osynit, WDE, Wicofe-Kernel, Wicofe-Tools and Wicofe-Build. Wicofe-Build consumes the Wicofe-Tools reusable audit workflow at an immutable commit. The table below lists distinct upstream action/workflow references with source/license evidence; repeated use by different consumers is counted separately in the 22-record total.

The upstream LICENSE files listed below were inspected at the stated source snapshots. No GPL/AGPL license text was identified in this limited action inventory. This is not a complete security, maintenance, transitive-action, or legal review. No action is marked approved.

## Upstream source and license evidence

| Consumer reference | Resolved source commit | Upstream license | License evidence |
|---|---|---|---|
| `Mattraks/delete-workflow-runs@v2` | `0cf693bc9909e5e867ee8f27b813224ba862939c` | MIT | [LICENSE](https://github.com/Mattraks/delete-workflow-runs/blob/0cf693bc9909e5e867ee8f27b813224ba862939c/LICENSE) |
| `actions/cache@v4` | `0057852bfaa89a56745cba8c7296529d2fc39830` | MIT | [LICENSE](https://github.com/actions/cache/blob/0057852bfaa89a56745cba8c7296529d2fc39830/LICENSE) |
| `actions/checkout@v4` | `11d5960a326750d5838078e36cf38b85af677262` | MIT | [LICENSE](https://github.com/actions/checkout/blob/11d5960a326750d5838078e36cf38b85af677262/LICENSE) |
| `actions/checkout@v6` | `d23441a48e516b6c34aea4fa41551a30e30af803` | MIT | [LICENSE](https://github.com/actions/checkout/blob/d23441a48e516b6c34aea4fa41551a30e30af803/LICENSE) |
| `actions/upload-artifact@v4` | `ea165f8d65b6e75b540449e92b4886f43607fa02` | MIT | [LICENSE](https://github.com/actions/upload-artifact/blob/ea165f8d65b6e75b540449e92b4886f43607fa02/LICENSE) |
| `actions/upload-artifact@v6` | `b7c566a772e6b6bfb58ed0dc250532a479d7789f` | MIT | [LICENSE](https://github.com/actions/upload-artifact/blob/b7c566a772e6b6bfb58ed0dc250532a479d7789f/LICENSE) |
| `actions/setup-python@v5` | `a26af69be951a213d495a4c3e4e4022e16d87065` | MIT | [LICENSE](https://github.com/actions/setup-python/blob/a26af69be951a213d495a4c3e4e4022e16d87065/LICENSE) |
| `actions/setup-python@v6` | `ece7cb06caefa5fff74198d8649806c4678c61a1` | MIT | [LICENSE](https://github.com/actions/setup-python/blob/ece7cb06caefa5fff74198d8649806c4678c61a1/LICENSE) |
| `android-actions/setup-android@v4` | `be39fa834029ff78f1a44aa3bb0819b8fc2bd8fd` | MIT | [LICENSE](https://github.com/android-actions/setup-android/blob/be39fa834029ff78f1a44aa3bb0819b8fc2bd8fd/LICENSE) |
| `dtolnay/rust-toolchain@stable` | `39008827e6b4319a349e9a42dfc90579dd25f1ca` | MIT | [LICENSE](https://github.com/dtolnay/rust-toolchain/blob/39008827e6b4319a349e9a42dfc90579dd25f1ca/LICENSE) |
| `reactivecircus/android-emulator-runner@v2` | `a421e43855164a8197daf9d8d40fe71c6996bb0d` | Apache-2.0 | [LICENSE](https://github.com/ReactiveCircus/android-emulator-runner/blob/a421e43855164a8197daf9d8d40fe71c6996bb0d/LICENSE) |
| `taiki-e/install-action@cross` | `af22fbf512bbc91a6a7869728037f907cc27e9d1` | MIT OR Apache-2.0 | [MIT](https://github.com/taiki-e/install-action/blob/af22fbf512bbc91a6a7869728037f907cc27e9d1/LICENSE-MIT) · [Apache-2.0](https://github.com/taiki-e/install-action/blob/af22fbf512bbc91a6a7869728037f907cc27e9d1/LICENSE-APACHE) |
| `Waizusora/Wicofe-Tools/.github/workflows/cross-repository-dependency-audit.yml` | `cccc4c197687ce8fd629f9b9d8a7d95d4e89cddc` | MPL-2.0 | [LICENSE](https://github.com/Waizusora/Wicofe-Tools/blob/cccc4c197687ce8fd629f9b9d8a7d95d4e89cddc/LICENSE) |


## Cross-repository scan snapshot — 2026-11-16

**Latest completed source/build evidence:** [Wicofe-Tools run 43881861767](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43881861767) · [artifact 14233016601](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43881861767/artifacts/14233016601)  
**Policy:** [Dependency License Policy 0.2](policies/DEPENDENCY_LICENSE_POLICY_0.2.md)

| Source/build finding | Result |
|---|---:|
| Repositories checked out and revision-recorded | 29 / 29 |
| Repositories with resolved Cargo manifests | 4 |
| Cargo.toml manifests | 16 |
| Transient Cargo.lock files generated in disposable CI checkouts | 4 |
| Total source/build dependency records | 347 |
| NEEDS_REVIEW | 243 |
| UNKNOWN | 102 |
| REJECTED | 2 |
| Cargo dependency records | 217 |
| GitHub Actions records | 22 |
| Build-tool command records | 72 |
| System-package references | 14 |
| Build-script command records | 12 |
| Runner-image records | 6 |
| Rust toolchain records | 3 |
| Downloaded-artifact records | 1 |
| Known vendored asset records | 2 (both UNKNOWN) |
| Git submodule records | 0 |

The four Cargo workspaces are Wicofe-Kernel, Osynit, WDE and Mysh. The 217 resolved external Cargo records are 216 for WDE and one for Osynit; the Mysh and Wicofe-Kernel Cargo manifests produced no external crate records in this snapshot. All 217 Cargo records are NEEDS_REVIEW, with no Cargo record classified GPL/AGPL REJECTED or PASS. The manifest inventory contains 23 records: 16 Cargo.toml, four Cargo.lock and three rust-toolchain.toml; no npm, Go, Maven, Gradle, CMake or Meson manifests were detected. Six repositories emitted source/build dependency records: Wicofe-Kernel (45), WDE (239), Mysh (32), Osynit (8), Wicofe-Tools (22) and Wicofe-Build (1 UNKNOWN). The other 23 repositories emitted no records; this is not a no-dependency approval.

### Additional CI package-closure evidence

These inventories are separate from the 347 source/build records above and must be reconciled before release.

| Repository | CI package records | REJECTED | NEEDS_REVIEW | UNKNOWN |
|---|---:|---:|---:|---:|
| Wicofe-Kernel | 103 | 15 | 84 | 4 |
| WDE | 32 | 0 | 19 | 13 |

Kernel CI artifact: [run 43882559388 / artifact 14233207628](https://github.com/Waizusora/Wicofe-Kernel/actions/runs/43882559388/artifacts/14233207628). The 15 rejected package records are `cpu-checker`, `ipxe-qemu`, `libburn4t64`, `libcdparanoia0`, `libfdt1`, `libfftw3-single3`, `libiscsi7`, `libisoburn1t64`, `libisofs6t64`, `libv4l-0t64`, `libv4lconvert0t64`, `libvte-2.91-0`, `libvte-2.91-common`, `msr-tools` and `xorriso`. The xorriso closure includes GPL `libburn4t64`, `libisoburn1t64` and `libisofs6t64`. The installed package delta still needs direct/transitive/recommended relationship mapping.

Sixty-three Kernel package records contain LGPL declarations: 27 primary LGPL, 26 MIXED_REVIEW, three OTHER_REVIEW and seven REJECTED because GPL is required. Three OR expressions are held at NEEDS_REVIEW: `ipxe-qemu-256k-compat-efi-roms` (GPL OR UBDL), `libflac14` (GPL OR LGPL), and `librdmacm1t64` (BSD-MIT OR GPL). QEMU's Debian package family uses the non-SPDX expression `GPL2-or-LGPL2-with-additions`; the package-level records remain NEEDS_REVIEW while the source-level scan conservatively rejects QEMU from upstream GPL COPYING evidence. QEMU remains blocked pending file/binary mapping.

WDE CI artifact: [run 43882021012 / artifact 14231069939](https://github.com/Waizusora/WDE/actions/runs/43882021012/artifacts/14231069939). Fourteen GLVND/Mesa package records have MIT as the primary `Files: *` license but GPL-3+ declarations in non-default copyright stanzas; all remain NEEDS_REVIEW pending binary payload mapping. Thirteen package identities remain UNKNOWN.

### Direct GPL host tools

Two direct GPL-2.0-or-later host-tool records remain release blockers under Policy 0.2:

| Dependency | Version | Function | Evidence |
|---|---|---|---|
| `qemu-system-x86` | `1:10.2.1+ds-1ubuntu3.3` | x86-64 BIOS boot validation | [QEMU COPYING](https://github.com/qemu/qemu/blob/2d3df8abca265c9bcc9e438d691d561592060998/COPYING) |
| `xorriso` | `1:1.5.6-1.1ubuntu4` | ISO generation and notice inspection | [libisoburn COPYING](https://github.com/Enzime/libisoburn/blob/master/COPYING) · [xorriso project](https://www.gnu.org/software/xorriso/) |

They are build/test host dependencies and are not copied into the final ISO. Policy 0.2 has no build-only exception. Do not remove them before permitted replacements preserve ISO and boot validation behavior.

### Candidate replacements under review

- QEMU → [Bochs 3.1](https://github.com/bochs-emu/Bochs/tree/REL_3_1_FINAL), immutable source commit `30cfd566ecc8deb33e56e801e32b444a7041b6d2`, [LGPL-2.1 LICENSE](https://github.com/bochs-emu/Bochs/blob/30cfd566ecc8deb33e56e801e32b444a7041b6d2/LICENSE). It supports x86-64 PC emulation; verify file-level notices, package closure, serial logging and boot-marker parity. It is not an AArch64 emulator.
- xorriso → [PyCdlib 1.22.0](https://pypi.org/project/pycdlib/), immutable source commit `fbf3079c6254054a1da03fccb1f84763f5f20b28`, [LGPL-2.1-only COPYING](https://github.com/clalancette/pycdlib/blob/fbf3079c6254054a1da03fccb1f84763f5f20b28/COPYING). Upstream documents El Torito ISO creation through a Python API. Verify BIOS boot-info-table, Rock Ridge/Joliet, volume metadata and boot parity. Do not use its upstream packaging test recipe unchanged because it references GPL genisoimage.
- xorriso → cdrtools/mkisofs (CDDL-1.0; explicit other-copyleft review/approval) or libisofs/libburn (LGPL-family; linking/relinking and notice review).

No candidate is approved. See the [detailed dependency review queue](DEPENDENCY_REVIEW_QUEUE_2026-11-16.md) for exact package versions, LGPL-bearing packages, optional license branches, UNKNOWN identities and decisions still required.

## Limine bootloader binary — Wicofe-Kernel

**Status:** NEEDS_REVIEW — upstream license and checksum evidence verified; owner approval and final ISO verification remain pending.

- Upstream: https://github.com/Limine-Bootloader/Limine
- Release: \`v12.9.6\`
- Source commit: \`89a9512c623a4779cc73e3869383876d54264b28\`
- Tag signature: verified
- Release archive: \`limine-binary.tar.xz\`
- SHA-256: \`939f670e0831cc940453fd3a0ddfb2b324c0b4e3c5d0e741c190aa0d13df0103\`
- Primary license: BSD-2-Clause ([COPYING](https://github.com/Limine-Bootloader/Limine/blob/89a9512c623a4779cc73e3869383876d54264b28/COPYING))
- Bundled notices: [3RDPARTY.md](https://github.com/Limine-Bootloader/Limine/blob/89a9512c623a4779cc73e3869383876d54264b28/3RDPARTY.md)

The reviewed upstream third-party notice lists 0BSD, BSD-2-Clause, MIT, Apache-2.0, CC0-1.0 and CC-BY-3.0-derived terms. No GPL/AGPL/LGPL identifier was found in the reviewed COPYING and 3RDPARTY.md documents. The detached archive signature has not been independently verified.

Wicofe-Kernel now vendors the exact upstream COPYING and 3RDPARTY.md files under \`third_party/licenses/limine-12.9.6/\`; its ISO build script requires them and stages them under \`/boot/limine/licenses/limine-12.9.6/\`. The ISO build has not yet been rerun and inspected after this change.

The script also uses host build tools including curl, make, tar, sha256sum and xorriso. Their versions, source provenance and build-environment image are not yet pinned. Limine's security/maintenance status is NOT_ASSESSED.


## Wicofe-Kernel package-closure review

The 103-package Kernel CI inventory is detailed in the cross-repository snapshot above and in [DEPENDENCY_REVIEW_QUEUE_2026-11-16.md](DEPENDENCY_REVIEW_QUEUE_2026-11-16.md). It includes 15 REJECTED packages, 84 NEEDS_REVIEW and four UNKNOWN. Twenty-seven packages have primary LGPL classification; 63 contain LGPL declarations across primary/secondary copyright stanzas. No LGPL approval is recorded.

The source-level scan rejects QEMU and xorriso. The package-level audit also exposes a custom QEMU package expression (`GPL2-or-LGPL2-with-additions`) requiring file/binary mapping. The current Kernel CI successfully uses these tools, but successful build/boot does not establish license compliance. Candidate alternatives remain Bochs (LGPL-2.1) and PyCdlib (LGPL-2.1-only), both requiring explicit review and parity tests.

## Required follow-up

1. Obtain explicit project-owner approval for each action/version under the consuming repository and release scope.
2. Pin all consumer workflow references to immutable commit SHAs. Wicofe-Tools workflows have been updated to SHA-pinned v6 actions; other repositories still contain mutable tag/branch references.
3. Review each action's own runtime dependencies, bundled JavaScript, downloaded tools and transitive supply chain.
4. Assess maintenance/security status, release provenance and tag-signature verification. The ReactiveCircus v2 annotated tag was unsigned at the inspected tag object.
5. Preserve required notices and include action licenses in the release compliance bundle.\n\nWicofe-Build now pins the reusable workflow file and auditor source checkout to `cccc4c197687ce8fd629f9b9d8a7d95d4e89cddc`. Wicofe-Kernel and WDE also pin this reviewed auditor revision for their package-license CI evidence. The reusable workflow and the tool source are therefore separately revision-pinned. The internal MPL-2.0 workflow still requires explicit review under Policy 0.2.

## Decision

All listed records remain **NEEDS_REVIEW**. Upstream license identification is evidence, not legal approval. The inventory does not establish that any action is distributed in the final Wicofe image.
