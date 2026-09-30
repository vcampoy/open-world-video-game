# Project State — Toolchain Verification

**Status:** Prompt 02 is **BLOCKED / PENDING HUMAN VALIDATION**. No project was opened or created, and no installation, download, license acceptance, or editor configuration was performed.

## Project

- **Project path:** `C:\Source\open-world-video-game`
- **Unity project structure:** Missing (`Assets/`, `Packages/`, and `ProjectSettings/` are absent). There is no project on which to verify opening, render pipeline selection, or package installation.
- **Game baseline:** See [GAME-BRIEF.md](GAME-BRIEF.md); prompt 01 passed in commit `973e998`.

## Toolchain facts (observed 2026-10-01)

| Component | Observed state | Notes |
|---|---|---|
| Unity Hub | **Installed**, version `3.22.0` | Found at `C:\Program Files\Unity Hub\Unity Hub.exe`. Account/license status was not inspected. |
| Unity Editor | **Installed**, version `6000.6.3f1` (`6000.6.3.4577518`) | This is a Unity 6.6 Update editor, not the proposed Unity 6.3 LTS line. Do not use it to create the project for this workflow. |
| Unity 6.3 LTS | **Missing** | Official archive lists `6000.3.24f1` (released 2026-09-10) as the latest verified 6.3 patch found in this check. Install from Unity Hub only after human approval. |
| Windows Build Support | **Installed for 6000.6.3f1** | `Editor\Data\PlaybackEngines\windowsstandalonesupport` exists. Its presence for the recommended 6000.3 editor is not verified. |
| C# IDE | **Installed**, Visual Studio Community 2026 `18.10.3` (`18.10.12224.181`) | The Unity game-development workload was not detected by Visual Studio Installer metadata. Editing a Unity script and Unity IDE integration have **not** been validated. VS Code is present, but its version/extensions could not be read because its CLI returned an access-denied error while trying to create the user settings directory. |
| Git | **Installed**, `2.54.0.windows.1` | Current branch: `codex/tiny-fantasy-island`, tracking `origin/codex/tiny-fantasy-island`. |
| Render pipeline | **Not configured** | No Unity project exists. **URP** remains the proposed pipeline for a new project; Unity’s 6000.3 docs list URP `17.3` as an Editor-matched core package. |

## Package Manager compatibility for proposed Unity 6.3 LTS (`6000.3`)

These are **verified official compatible sources, not installed project packages**. Package status remains **needed later / not installed**, because no project exists.

| Package | Compatible released version for 6000.3 | Purpose | State |
|---|---:|---|---|
| Input System (`com.unity.inputsystem`) | `1.20.0` | Keyboard/mouse action-based input. | Needed later; not installed in a project. |
| Cinemachine (`com.unity.cinemachine`) | `3.1.7` | Camera rigs and follow/orbit behavior. | Needed later; not installed in a project. |
| AI Navigation (`com.unity.ai.navigation`) | `2.0.15` | NavMesh pathfinding and navigation components for enemies. | Needed later; not installed in a project. |
| Unity Test Framework (`com.unity.test-framework`) | Editor-bound core package; Unity 6000.3 docs link package documentation `1.6` and state core package versions match the Editor. The exact patch version is not stated on that Manual page. | Edit Mode and Play Mode tests. | Needed later; not installed in a project. |

URP `17.3` is an Editor-matched core package for 6000.3. It will be part of the new URP project template/pipeline choice, not a separately verified install in this empty checkout.

## Checks and evidence

- [x] Unity Hub and installed Editor identified, with exact versions.
- [x] Windows build support confirmed for installed Editor `6000.6.3f1` only.
- [x] Visual Studio and Git versions identified.
- [x] Official Unity Package Manager compatibility checked for proposed Unity `6000.3` LTS.
- [ ] Project opens — **PENDING HUMAN VALIDATION**; no Unity project exists.
- [ ] IDE edits a Unity C# script — **PENDING HUMAN VALIDATION**; Unity workload/integration not verified.
- [ ] Windows build support exists for Unity `6000.3` — **PENDING HUMAN VALIDATION**.
- [ ] Needed compatible packages are visible/available in Package Manager — official compatible sources are verified, but actual project Package Manager availability is **PENDING HUMAN VALIDATION**.
- [ ] Unity Hub account/license/terms status — **PENDING HUMAN VALIDATION**; no license acceptance performed.

## Human setup required before prompt 03

1. In Unity Hub, install **Unity 6.3 LTS `6000.3.24f1`** (or a newer 6000.3 patch if Hub offers one), including **Windows Build Support**. Do not uninstall or upgrade the existing 6000.6.3f1 editor.
2. In Visual Studio Installer, install the Unity/game-development workload if it is missing; then verify Visual Studio is selected as Unity’s external script editor and can open/edit a generated C# script.
3. Open Unity Hub and verify the account/license prompt. Accept applicable license/terms yourself; no purchase is recommended or authorized here.
4. After a human confirms the above, create/open the new Unity 6.3 LTS URP project and verify it opens and Package Manager lists the documented compatible package versions. Keep this pending until those checks are confirmed.

## Changes and next phase

- **Files changed this phase:** `docs/PROJECT-STATE.md` only.
- **No gameplay code or Unity project files changed.**
- **Next eligible phase:** Prompt 03 remains blocked until the missing editor/workload setup and required human validations above are complete.

## Official references

- [Unity 6 release support](https://unity.com/releases/unity-6/support) — Unity 6.3 LTS support horizon and Update/LTS distinction.
- [Unity 6000.3.24f1 release notes](https://unity.com/releases/editor/whats-new/6000.3.24f1) — exact recommended patch found.
- [Input System for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.inputsystem.html)
- [Cinemachine for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.cinemachine.html)
- [AI Navigation for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.ai.navigation.html)
- [Test Framework for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.test-framework.html)
- [URP for Unity 6000.3](https://docs.unity3d.com/6000.3/Documentation/Manual/com.unity.render-pipelines.universal.html)
