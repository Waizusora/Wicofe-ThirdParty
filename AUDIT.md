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
| `Waizusora/Wicofe-Tools/.github/workflows/cross-repository-dependency-audit.yml` | `ca5e5747c7f92921c24f03a56d42a27a5f0c1c52` | MPL-2.0 | [LICENSE](https://github.com/Waizusora/Wicofe-Tools/blob/ca5e5747c7f92921c24f03a56d42a27a5f0c1c52/LICENSE) |

## Required follow-up

1. Obtain explicit project-owner approval for each action/version under the consuming repository and release scope.
2. Pin all consumer workflow references to immutable commit SHAs. Wicofe-Tools workflows have been updated to SHA-pinned v6 actions; other repositories still contain mutable tag/branch references.
3. Review each action's own runtime dependencies, bundled JavaScript, downloaded tools and transitive supply chain.
4. Assess maintenance/security status, release provenance and tag-signature verification. The ReactiveCircus v2 annotated tag was unsigned at the inspected tag object.
5. Preserve required notices and include action licenses in the release compliance bundle.

## Decision

All listed records remain **NEEDS_REVIEW**. Upstream license identification is evidence, not legal approval. The inventory does not establish that any action is distributed in the final Wicofe image.
