# CI Action Dependency Inventory

**Audit date:** 2026-11-16  
**Policy:** [Wicofe Dependency License Policy 0.2](policies/DEPENDENCY_LICENSE_POLICY_0.2.md)  
**Status:** Evidence collected; all entries remain NEEDS_REVIEW until owner approval and consumer pinning are verified.

## Scope and result

The cross-repository scanner found external GitHub Actions in Mysh, Osynit, WDE, Wicofe-Kernel and Wicofe-Tools. Wicofe-Build now consumes the Wicofe-Tools reusable audit workflow at an immutable commit.

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
| `Waizusora/Wicofe-Tools/.github/workflows/cross-repository-dependency-audit.yml` | `ad1175c000c765834045a0035fae3cb0b4a49374` | MPL-2.0 | [LICENSE](https://github.com/Waizusora/Wicofe-Tools/blob/ad1175c000c765834045a0035fae3cb0b4a49374/LICENSE) |


## Cross-repository scan snapshot — 2026-11-16

**Latest completed evidence run:** [Wicofe-Tools run 43877691846](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43877691846)  
**Artifact:** [29-repository JSON/Markdown reports and Cargo metadata](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43877691846/artifacts/14231895200)  
**Policy:** [Dependency License Policy 0.2](policies/DEPENDENCY_LICENSE_POLICY_0.2.md)

| Finding | Result |
|---|---:|
| Repositories checked out and revision-recorded | 29 / 29 |
| Repositories with resolved Cargo manifests | 4 |
| Cargo.toml manifests | 16 |
| Transient Cargo.lock files generated in disposable CI checkouts | 4 |
| Total dependency/build-time records | 347 |
| NEEDS_REVIEW | 244 |
| UNKNOWN | 101 |
| REJECTED | 2 |
| Cargo dependency records | 217 |
| GitHub Actions records | 22 |
| Build-tool command records | 72 |
| System-package records | 14 |
| Build-script command records | 12 |
| Runner-image records | 6 |
| Rust toolchain records | 3 |
| Downloaded-artifact records | 1 |
| Known vendored asset records | 2 (both UNKNOWN) |
| Git submodule records | 0 |

Cargo workspaces/packages audited: Wicofe-Kernel, Osynit, WDE and Mysh. The 217 Cargo records are part of the larger 347-record inventory; the remaining records cover GitHub Actions, build commands, system packages, runner images, toolchains and downloaded artifacts. Four transient lockfiles were generated in disposable CI checkouts and uploaded as evidence. They were not committed to source repositories.

Six repositories emitted dependency/build-time records: Wicofe-Kernel (45), WDE (239), Mysh (32), Osynit (8), Wicofe-Tools (22) and Wicofe-Build (1). The other 23 repositories emitted no dependency records in this run; that is not a no-dependency approval. Repositories without resolved Cargo manifest coverage remain UNKNOWN pending complete source/build/asset inspection and human attestation where justified.

### Prohibited GPL host tools

Two GPL-2.0-or-later host packages were detected in Wicofe-Kernel CI and are **REJECTED** under Policy 0.2:

| Dependency | Version | Function | Evidence |
|---|---|---|---|
| `qemu-system-x86` | `1:10.2.1+ds-1ubuntu3.3` | x86-64 BIOS boot validation | [QEMU COPYING](https://github.com/qemu/qemu/blob/2d3df8abca265c9bcc9e438d691d561592060998/COPYING) |
| `xorriso` | `1:1.5.6-1.1ubuntu4` | ISO generation and ISO notice inspection | [libisoburn COPYING](https://github.com/Enzime/libisoburn/blob/master/COPYING) · [xorriso project](https://www.gnu.org/software/xorriso/) |

They are build/test host dependencies and are not copied into the final ISO, but Policy 0.2 does not provide a build-only exception. They remain release blockers. They have not been removed because they currently provide required ISO-generation and boot-validation functionality.

Candidate replacements already identified:
- QEMU → Bochs (LGPL-2.1; explicit conditional approval and x86 boot-log parity tests required; not an AArch64 replacement).
- xorriso → cdrtools/mkisofs (CDDL-1.0; explicit other-copyleft review/approval required) or libisofs/libburn (LGPL-family; linking/relinking and notice obligations require review).

No candidate is approved by this report. A replacement must be tested before the GPL tool is removed.

### Remaining status

All 244 NEEDS_REVIEW records lack the required scoped approval. All 101 UNKNOWN records lack sufficient evidence or a resolved source/license identity. Two known vendored Limine notice files remain UNKNOWN as asset records until their component/source/binary distribution relationship is fully reconciled. The current scan does not prove the absence of other firmware, fonts, codecs, schemas, generated files or binary assets.

Wicofe-Build contains a reusable/tag-triggered strict dependency gate that invokes the Wicofe-Tools cross-repository workflow at an immutable workflow revision and separately pins the auditor source. This integration point does not yet constitute a complete end-to-end image publication gate. Final image SBOM and notice reconciliation remain mandatory.

This snapshot is not a Wicofe OS compliance certification.

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


## Wicofe-Kernel CI host-tool blockers

The pinned kernel CI environment installs and uses the following GPL build/test tools. They are not copied into the Wicofe ISO, but Policy 0.2 has no documented build-only exception, so the auditor treats them as REJECTED and release-blocking rather than silently exempting them.

| Dependency | Pinned version | Function | License decision |
|---|---|---|---|
| \`qemu-system-x86\` | \`1:10.2.1+ds-1ubuntu3.3\` | BIOS boot test | REJECTED — GPL-2.0-or-later |
| \`xorriso\` | \`1:1.5.6-1.1ubuntu4\` | ISO creation | REJECTED — GPL-2.0-or-later |

The toolchain remediation already removed GNU Make, GNU tar, GNU coreutils \`sha256sum\`, and GNU binutils \`readelf\` from the active kernel build steps:
- Limine host utility is compiled from the root-level C99 source in the pinned binary archive using Clang 22; GNU Make is not invoked.
- SHA-256 verification and safe archive extraction use Python standard-library \`hashlib\` and \`tarfile\`.
- ELF inspection uses \`llvm-readelf-22\`.

Remaining alternatives under evaluation:
- QEMU → Bochs (LGPL-2.1; x86 PC emulator, not an AArch64 replacement). Requires LGPL review/approval and boot-log parity tests.
- xorriso → cdrtools/mkisofs (CDDL-1.0; explicit copyleft review/approval) or libisofs/libburn (LGPL-family; linking/relinking and notice obligations require review).
- LLVM 22 tools use Apache-2.0 WITH LLVM-exception; verify package-level notices from the CI system-package inventory before approval.

The current QEMU and xorriso uses remain release blockers until a permitted replacement is validated or the policy scope is explicitly revised by its owner. They have not been removed because they currently provide the working ISO-generation and boot-validation path.

## Required follow-up

1. Obtain explicit project-owner approval for each action/version under the consuming repository and release scope.
2. Pin all consumer workflow references to immutable commit SHAs. Wicofe-Tools workflows have been updated to SHA-pinned v6 actions; other repositories still contain mutable tag/branch references.
3. Review each action's own runtime dependencies, bundled JavaScript, downloaded tools and transitive supply chain.
4. Assess maintenance/security status, release provenance and tag-signature verification. The ReactiveCircus v2 annotated tag was unsigned at the inspected tag object.
5. Preserve required notices and include action licenses in the release compliance bundle.\n\nWicofe-Build now pins the reusable workflow file at `ad1175c000c765834045a0035fae3cb0b4a49374` and passes the auditor source checkout pin `b459eb9dd80b265183bff4dc518d82ad73321150`. The reusable workflow and the tool source are therefore separately revision-pinned. The internal MPL-2.0 workflow still requires explicit review under Policy 0.2.

## Decision

All listed records remain **NEEDS_REVIEW**. Upstream license identification is evidence, not legal approval. The inventory does not establish that any action is distributed in the final Wicofe image.
