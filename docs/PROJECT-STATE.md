# Project State — Toolchain Verification

**Status:** Prompt 02 remains **BLOCKED / PENDING HUMAN VALIDATION**. On 2026-10-01, after the user authorized project creation using the installed Unity 6.6 Editor, a prompt-03 bootstrap was attempted but **BLOCKED before project initialization completed**. No license acceptance or purchase was performed.

## Project

- **Project path:** `C:\Source\open-world-video-game`
- **Unity project structure:** Partial bootstrap only: `Assets/` exists but is empty, `ProjectSettings/` was generated, and `Packages/` is absent. Treat this as **not yet a usable/opened Unity project**; no scene, URP asset, package manifest, or build exists.
- **Game baseline:** See [GAME-BRIEF.md](GAME-BRIEF.md); prompt 01 passed in commit `973e998`.

## Toolchain facts (observed 2026-10-01)

| Component | Observed state | Notes |
|---|---|---|
| Unity Hub | **Installed**, version `3.22.0` | Found at `C:\Program Files\Unity Hub\Unity Hub.exe`. Account/license status was not inspected. |
| Unity Editor | **Installed**, version `6000.6.3f1` (`6000.6.3.4577518`) | Unity 6.6 Update, production-ready. It is a technically viable new-project choice; it is not LTS and has a shorter support window. |
| Unity 6.3 LTS | **Not installed / not selected** | Prompt 02 proposed `6000.3.24f1` as its LTS default. The user chose to proceed with the already-installed Unity 6.6 Update for this new project, so no additional Editor installation is currently needed. |
| Windows Build Support | **Installed for 6000.6.3f1** | `Editor\Data\PlaybackEngines\windowsstandalonesupport` exists. Presence for `6000.3` is not verified. |
| C# IDE | **Installed**, Visual Studio Community 2026 `18.10.3` (`18.10.12224.181`) | The Unity game-development workload was not detected by Visual Studio Installer metadata. Editing a Unity script and Unity IDE integration have **not** been validated. VS Code is present, but its version/extensions could not be read because its CLI returned an access-denied error while trying to create the user settings directory. |
| Git | **Installed**, `2.54.0.windows.1` | Current branch: `codex/tiny-fantasy-island`, tracking `origin/codex/tiny-fantasy-island`. |
| Render pipeline | **Not configured** | **URP** is the selected pipeline for the new project; Unity’s 6000.6 docs identify URP `17.6` as an Editor-matched core package. |

## Bootstrap attempt (2026-10-01)

- Used the installed Unity `6000.6.3f1` Editor's documented `-createProject` option at the repository root. Unity created `ProjectSettings/` and an empty `Assets/`, but did not create `Packages/` or finish opening the project.
- The log `C:\Source\open-world-video-game\UnityCreate.log` records `LicenseClient-dante` IPC connection refusals and licensing initialization timeouts. The Editor process was stopped after it remained waiting; no files were deleted.
- **Result:** no project-open, URP, scene-reference, compilation, or standalone-build check passed. No gameplay or scene content was created.
- **Git ignore correction:** `.gitignore` no longer excludes Unity `.meta` files, `.obj` source assets, or the Unity `Packages/` manifest/lock files; Unity caches and build folders are ignored.

## Package Manager compatibility

These are **verified official compatible sources, not installed project packages**. Package status remains **needed later / not installed**, because no project exists.

| Package | Unity 6.3 LTS (`6000.3`) | Installed Unity 6.6 (`6000.6`) | Purpose / state |
|---|---:|---|---|
| Input System (`com.unity.inputsystem`) | `1.20.0` released | `1.20.0` released | Keyboard/mouse action-based input; needed later, not installed in a project. |
| Cinemachine (`com.unity.cinemachine`) | `3.1.7` released | Editor-matched core package; 6000.6 docs link `6.6` | Camera rigs and follow/orbit behavior; needed later, not installed in a project. |
| AI Navigation (`com.unity.ai.navigation`) | `2.0.15` released | `2.0.15` released | NavMesh pathfinding and navigation components for enemies; needed later, not installed in a project. |
| Unity Test Framework (`com.unity.test-framework`) | Editor-matched core package; docs link `1.6` | Editor-matched core package; docs link `1.8` | Edit Mode and Play Mode tests; needed later, not installed in a project. |

URP is the proposed render pipeline. It is an Editor-matched core package (`17.3` for 6000.3; `17.6` for 6000.6). It will be selected for the new project, not separately installed in this empty checkout. Unity describes Update releases as production-ready and recommends them for new or mid-cycle projects; LTS has a longer support window.

## Checks and evidence

- [x] Unity Hub and installed Editor identified, with exact versions.
- [x] Windows build support confirmed for installed Editor `6000.6.3f1` only.
- [x] Visual Studio and Git versions identified.
- [x] Official Unity Package Manager compatibility checked for both proposed `6000.3` LTS and installed `6000.6` Editor.
- [ ] Project opens — **BLOCKED / PENDING HUMAN VALIDATION**; only partial bootstrap files exist, and Editor licensing initialization did not complete.
- [ ] IDE edits a Unity C# script — **PENDING HUMAN VALIDATION**; Unity workload/integration not verified.
- [ ] Windows build support exists for Unity `6000.3` — **PENDING HUMAN VALIDATION**.
- [ ] Needed compatible packages are visible/available in Package Manager — official compatible sources are verified for both editor lines, but actual project Package Manager availability is **PENDING HUMAN VALIDATION**.
- [ ] Unity Hub account/license/terms status — **PENDING HUMAN VALIDATION**; Editor reported Licensing Client IPC/timeouts; no license acceptance performed.

## Human setup required to resume prompt 03

1. In Unity Hub, sign in and complete any eligible license activation/terms step yourself. Do not purchase anything for this project.
2. Once licensing is active, resume prompt 03: finish creating/opening the Unity 6.6 URP project, then verify Package Manager and Editor startup.
3. Verify Visual Studio is selected as Unity’s external script editor and can open/edit a generated C# script. The Unity/game-development workload was not detected by Visual Studio Installer metadata; install it only if this manual check fails or its Unity support is absent.
4. Keep all checks pending until confirmed.

## Changes and next phase

- **Files changed this phase:** `.gitignore` and `docs/PROJECT-STATE.md`. The failed bootstrap left an incomplete, untracked `ProjectSettings/` directory; it is not a usable Unity project and must not be treated as a completed scaffold.
- **No gameplay code, scene, or build was created.**
- **Next eligible phase:** Prompt 03 remains blocked until Unity Hub licensing is active; then finish the scaffold and verify the required checks above.

## Official references

- [Unity 6 release support](https://unity.com/releases/unity-6/support) — Unity 6.3 LTS support horizon and Update/LTS distinction.
- [Unity 6000.3.24f1 release notes](https://unity.com/releases/editor/whats-new/6000.3.24f1) — exact recommended patch found.
- [Input System for Unity 6000.6](https://docs.unity3d.com/6000.6/Documentation/Manual/com.unity.inputsystem.html)
- [Cinemachine for Unity 6000.6](https://docs.unity3d.com/6000.6/Documentation/Manual/com.unity.cinemachine.html)
- [AI Navigation for Unity 6000.6](https://docs.unity3d.com/6000.6/Documentation/Manual/com.unity.ai.navigation.html)
- [Test Framework for Unity 6000.6](https://docs.unity3d.com/6000.6/Documentation/Manual/com.unity.test-framework.html)
- [URP for Unity 6000.6](https://docs.unity3d.com/6000.6/Documentation/Manual/com.unity.render-pipelines.universal.html)
- [Input System for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.inputsystem.html)
- [Cinemachine for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.cinemachine.html)
- [AI Navigation for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.ai.navigation.html)
- [Test Framework for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.test-framework.html)
- [URP for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.render-pipelines.universal.html)
