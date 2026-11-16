# Wicofe Dependency License Review Queue — 2026-11-16

**Policy:** [Dependency License Policy 0.2](policies/DEPENDENCY_LICENSE_POLICY_0.2.md)  
**Latest cross-repository evidence:** [Wicofe-Tools run 43881861767](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43881861767) · [artifact 14233016601](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43881861767/artifacts/14233016601)  
**Additional CI package evidence:** [Wicofe-Kernel run 43882559388 / artifact 14233207628](https://github.com/Waizusora/Wicofe-Kernel/actions/runs/43882559388/artifacts/14233207628) · [WDE run 43882021012 / artifact 14231069939](https://github.com/Waizusora/WDE/actions/runs/43882021012/artifacts/14231069939)  
**Overall result:** BLOCKED. This queue is evidence triage, not legal approval.

## 1. Status summary

### Cross-repository source/build inventory

| Status | Records | Decision |
|---|---:|---|
| REJECTED | 2 | Direct GPL source/build records; replace or resolve |
| NEEDS_REVIEW | 243 | No scoped decision recorded |
| UNKNOWN | 102 | Source/license identity or evidence incomplete |
| PASS / APPROVED_WITH_CONDITIONS | 0 | No approved records in this snapshot |
| **Total** | **347** | **BLOCKED** |

The 347 records include 217 Cargo records (216 WDE, one Osynit; no external crate records in the Mysh or Kernel Cargo graphs), 22 GitHub Actions, 72 build-tool command records, 14 system-package references, 12 build-script command records, six runner images, three Rust toolchain records and one downloaded artifact. All 217 Cargo records are NEEDS_REVIEW; none is GPL/AGPL REJECTED or PASS.

### Additional per-repository CI system-package inventories

These package records are separate from, and not merged into, the 347 source/build records above.

| Repository | Package records | REJECTED | NEEDS_REVIEW | UNKNOWN |
|---|---:|---:|---:|---:|
| Wicofe-Kernel | 103 | 15 | 84 | 4 |
| WDE | 32 | 0 | 19 | 13 |

## 2. Replacement queue — prohibited GPL

Two direct GPL host-tool records are detected in Wicofe-Kernel's source/build scan:

| Component | Version | Current role | License |
|---|---|---|---|
| `qemu-system-x86` | `1:10.2.1+ds-1ubuntu3.3` | x86-64 BIOS boot validation | Upstream source evidence GPL-2.0-or-later; Debian package copyright has a custom mixed expression that still needs file/binary mapping |
| `xorriso` | `1:1.5.6-1.1ubuntu4` | ISO generation and ISO notice inspection | GPL-2.0-or-later |

The Kernel CI package-delta artifact additionally records 15 REJECTED installed packages:

| Package | Version | Primary license evidence |
|---|---|---|
| `cpu-checker` | `0.7-1.4build1` | GPL-3 |
| `ipxe-qemu` | `1.21.1+git-20250829.969ce2c55+dfsg-3ubuntu2` | GPL-2+ |
| `libburn4t64` | `1.5.6-1.2build1` | GPL-2+ |
| `libcdparanoia0` | `3.10.2+debian-14ubuntu2` | GPL-2+ |
| `libfdt1` | `1.7.2-2ubuntu1` | GPL-2+ |
| `libfftw3-single3` | `3.3.10-2fakesync1build3` | GPL-2+ |
| `libiscsi7` | `1.20.0-4build1` | GPL-2+ |
| `libisoburn1t64` | `1:1.5.6-1.1ubuntu4` | GPL-2+ |
| `libisofs6t64` | `1.5.6.pl01-1.1ubuntu3` | GPL-2+ |
| `libv4l-0t64` | `1.32.0-2ubuntu1` | GPL-2 |
| `libv4lconvert0t64` | `1.32.0-2ubuntu1` | GPL-2 |
| `libvte-2.91-0` | `0.84.0-2` | GPL-3+ AND LGPL-3+ AND Expat |
| `libvte-2.91-common` | `0.84.0-2` | GPL-3+ AND LGPL-3+ AND Expat |
| `msr-tools` | `1.3+git20220805.7d78c80-1ubuntu0.1` | GPL-2 |
| `xorriso` | `1:1.5.6-1.1ubuntu4` | GPL-2+ |

The 103 package records are the installed CI package delta, not a proven minimal direct/transitive/recommended closure. Map package edges and actual usage before deciding which packages can be removed by using a minimal headless package set. The xorriso stack directly includes GPL packages `libburn4t64`, `libisoburn1t64` and `libisofs6t64`.

`libfdt1` remains REJECTED because its primary `Files: *` declaration is GPL-2+; a BSD declaration in another file stanza does not establish that the installed library payload is selectable under BSD. The QEMU package family has a custom `GPL2-or-LGPL2-with-additions` package expression; package-level records remain NEEDS_REVIEW while the source-level scanner rejects QEMU from upstream GPL COPYING evidence. Keep QEMU blocked until file/binary mapping resolves this discrepancy.

## 3. LGPL inventory — Kernel CI package closure

Sixty-three Kernel CI package records contain LGPL declarations:
- 27 have primary scanner category LGPL: 18 carry LGPL SPDX-like expressions, while nine QEMU-family records use the custom, unverified `GPL2-or-LGPL2-with-additions` expression and must not be treated as confirmed LGPL approvals.
- 26 are MIXED_REVIEW.
- 3 are OTHER_REVIEW.
- 7 are REJECTED because their primary/required license is GPL.

The 27 primary-LGPL package records are:

| Package | Version | Primary expression |
|---|---|---|
| `glib-networking-common` | `2.80.1-1build2` | LGPL-2+ AND LGPL-2.1+ |
| `glib-networking-services` | `2.80.1-1build2` | LGPL-2+ AND LGPL-2.1+ |
| `glib-networking` | `2.80.1-1build2` | LGPL-2+ AND LGPL-2.1+ |
| `gsettings-desktop-schemas` | `50.0-1ubuntu2` | LGPL-2.1+ |
| `gstreamer1.0-plugins-base` | `1.28.2-1ubuntu0.2` | LGPL-2+ |
| `gstreamer1.0-plugins-good` | `1.28.2-2ubuntu0.4` | LGPL-2+ |
| `gstreamer1.0-x` | `1.28.2-1ubuntu0.2` | LGPL-2+ |
| `libaa1` | `1.4p5-51.1build1` | LGPL-2.0+ |
| `libasyncns0` | `0.8-7` | LGPL-2.1+ |
| `libgstreamer-plugins-base1.0-0` | `1.28.2-1ubuntu0.2` | LGPL-2+ |
| `libmpg123-0t64` | `1.33.3-2` | LGPL-2.1 |
| `libsoup-3.0-0` | `3.6.6-1ubuntu0.3` | LGPL-2+ |
| `libsoup-3.0-common` | `3.6.6-1ubuntu0.3` | LGPL-2+ |
| `libspice-server1` | `0.16.0-1` | LGPL-2.1+ |
| `libssh-4` | `0.11.3-1ubuntu2.1` | LGPL-2.1+ with OpenSSL terms |
| `libtag2` | `2.2.1-3` | LGPL-2.1 OR MPL-1.1 |
| `libtwolame0` | `0.4.0-2build4` | LGPL-2+ |
| `qemu-block-extra` | `1:10.2.1+ds-1ubuntu3.3` | GPL2-or-LGPL2-with-additions |
| `qemu-system-common` | `1:10.2.1+ds-1ubuntu3.3` | GPL2-or-LGPL2-with-additions |
| `qemu-system-data` | `1:10.2.1+ds-1ubuntu3.3` | GPL2-or-LGPL2-with-additions |
| `qemu-system-gui` | `1:10.2.1+ds-1ubuntu3.3` | GPL2-or-LGPL2-with-additions |
| `qemu-system-modules-opengl` | `1:10.2.1+ds-1ubuntu3.3` | GPL2-or-LGPL2-with-additions |
| `qemu-system-modules-spice` | `1:10.2.1+ds-1ubuntu3.3` | GPL2-or-LGPL2-with-additions |
| `qemu-system-x86` | `1:10.2.1+ds-1ubuntu3.3` | GPL2-or-LGPL2-with-additions |
| `qemu-utils` | `1:10.2.1+ds-1ubuntu3.3` | GPL2-or-LGPL2-with-additions |
| `ubuntu-virt` | `1:10.2.1+ds-1ubuntu3.3` | GPL2-or-LGPL2-with-additions |
| `user-session-migration` | `0.5.1` | LGPL-3+ |

The 26 MIXED_REVIEW records with LGPL declarations are `libavc1394-0`, `libcaca0`, `libcacard0`, `libdaxctl1`, `libdv4t64`, `libflac14`, `libiec61883-0`, `libjack-jackd2-0`, `libmp3lame0`, `libndctl6`, `libnfs14`, `libpipewire-0.3-0t64`, `libpipewire-0.3-common`, `libproxy1v5`, `libpulse0`, `librados2`, `librbd1`, `libshout3`, `libsndfile1`, `libspa-0.2-modules`, `libtheora1`, `libtheoradec2`, `libtheoraenc2`, `libusbredirparser1t64`, `libvisual-0.4-0` and `ubuntu-helper-virt-hwe`.

The three OTHER_REVIEW records with LGPL declarations are `libsdl2-2.0-0`, `libsdl2-classic` and `libspeex1`. The seven GPL-required records that also contain LGPL declarations are `libcdparanoia0`, `libfdt1`, `libiscsi7`, `libv4l-0t64`, `libv4lconvert0t64`, `libvte-2.91-0` and `libvte-2.91-common`; they remain REJECTED. All non-rejected LGPL/mixed records remain NEEDS_REVIEW. No LGPL package has explicit approval or verified relinking/source/notices conditions in the decision registry.

## 4. Multi-license OR alternatives requiring human selection

These records must not be automatically rejected solely because one OR branch is GPL, but they are not approved:

| Package | Version | Expression | Non-GPL branch |
|---|---|---|---|
| `ipxe-qemu-256k-compat-efi-roms` | `1.0.0+git-20150424.a25a16d-0ubuntu7` | GPL-2+ OR UBDL | UBDL — custom/ambiguous; explicit approval required |
| `libflac14` | `1.5.0+ds-5` | GPL-2+ OR LGPL-2.1+ | LGPL-2.1+ — full LGPL review/approval |
| `librdmacm1t64` | `61.0-2ubuntu3` | BSD-MIT OR GPL-2 | BSD-MIT — exact notice/compatibility review |

`libfdt1` is not in this table because its primary license is GPL-2+; a secondary BSD stanza does not prove the installed library's default payload is BSD.

## 5. WDE system-package inventory

WDE CI recorded 32 package records: 19 NEEDS_REVIEW, 13 UNKNOWN and zero REJECTED. Fourteen GLVND/Mesa packages have MIT as the primary `Files: *` license but GPL-3+ in non-default copyright stanzas; map the actual installed binary payload before approving.

The 13 UNKNOWN identities are `libx11-dev`, `libxau-dev`, `libxcb1-dev`, `libxcursor-dev`, `libxext-dev`, `libxfixes-dev`, `libxi-dev`, `libxinerama-dev`, `libxkbcommon-dev`, `libxrandr-dev`, `libxrender-dev`, `xorg-sgml-doctools` and `xtrans-dev`.

## 6. LGPL-bearing Cargo alternatives — WDE

The WDE Cargo graph contains two `r-efi` versions with the expression `MIT OR Apache-2.0 OR LGPL-2.1-or-later`:

| Package | Version | Parent | Target condition | Checksum |
|---|---|---|---|---|
| `r-efi` | 5.3.0 | `getrandom 0.3.4` | UEFI / `efi_rng` | `69cdb34c158ceb288df11e18b4bd39de994f6657d83847bdffdbd7f346754b0f` |
| `r-efi` | 6.0.0 | `getrandom 0.4.3` | UEFI / `efi_rng` | `f8dcc9c7d52a811697d2151c701e0d08956f92b0e24136cf4cf27b57a6a0d9bf` |

Upstream: [r-efi/r-efi](https://github.com/r-efi/r-efi). These are target-conditioned edges from all-target metadata, not evidence that the current Linux WDE build links LGPL. The supported target matrix and exact selected branch still require review. The auditor never selects MIT/Apache automatically.

## 7. UNKNOWN inventory

The cross-repository scanner reports 102 UNKNOWN source/build records. The Kernel package inventory adds four UNKNOWN package records: `libbrlapi0.8`, `liborc-0.4-0t64`, `libraw1394-11` and `seabios`. WDE adds the 13 package identities listed in §5.

Unknown records are held until exact source package/version, source repository, license/copyright text, build/usage relationship and distribution scope are established. A package name or runner label is not license evidence.

## 8. Replacement candidate review

- QEMU → [Bochs 3.1](https://github.com/bochs-emu/Bochs/tree/REL_3_1_FINAL), immutable source commit `30cfd566ecc8deb33e56e801e32b444a7041b6d2`, [LGPL-2.1 LICENSE](https://github.com/bochs-emu/Bochs/blob/30cfd566ecc8deb33e56e801e32b444a7041b6d2/LICENSE). It supports x86-64 PC emulation; verify per-file notices, package closure, serial logging and boot-marker parity. It does not replace an AArch64 emulator.
- xorriso → [PyCdlib 1.22.0](https://pypi.org/project/pycdlib/), immutable source commit `fbf3079c6254054a1da03fccb1f84763f5f20b28`, [LGPL-2.1-only COPYING](https://github.com/clalancette/pycdlib/blob/fbf3079c6254054a1da03fccb1f84763f5f20b28/COPYING). Upstream documents El Torito ISO creation through a Python API. Verify BIOS boot-info-table, Rock Ridge/Joliet, volume metadata and boot parity. Do not use its upstream packaging test recipe unchanged because it references GPL genisoimage.
- xorriso → cdrtools/mkisofs (CDDL-1.0; explicit other-copyleft review/approval) or libisofs/libburn (LGPL-family; linking/relinking and notice review).

No candidate is approved. All require exact source/license and dependency-closure review before integration.

## 9. Approved inventory

**Zero dependencies were marked PASS or APPROVED_WITH_CONDITIONS in these evidence snapshots.**

The example decision registry is intentionally empty. Do not populate it until technical and license review is completed and an authorized human decision records exact scope, reviewer, approver, evidence, selected license branch and conditions. For LGPL, verify source/relinking obligations, notices, distribution model, linking method and replacement capability before marking conditions verified.

## 10. Release gate and remaining gaps

The strict cross-repository run [43881861767](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43881861767) failed closed and uploaded artifact [14233016601](https://github.com/Waizusora/Wicofe-Tools/actions/runs/43881861767/artifacts/14233016601). Kernel and WDE CI package artifacts are additional evidence and are not yet automatically reconciled by the Wicofe-Build release gate.

Vendored firmware, fonts, codecs, schemas, generated code, binary assets and final image contents still require inventory. Security and maintenance status remain NOT_ASSESSED for all records unless explicitly recorded in the artifact/decision record.

**No Wicofe-wide license-compliance claim is made.**
