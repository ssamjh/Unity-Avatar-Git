## Model routing
- You own planning, architecture, and final verification. Don't write bulk code yourself.
- Break work into independent, clearly scoped tasks with success criteria and hand each to a subagent.
- Review subagent output before reporting done.

## Project purpose and layout
- This repository provides reusable Git configuration templates for Unity and VRChat projects; it is not itself an avatar project.
- `templates/.gitignore` and `templates/.gitattributes` are copied into a Unity project root. Root `.gitignore` and `.gitattributes` govern this template repository only.
- `README.md` is the user-facing guide. Keep it consistent with the templates and this file.
- There is no Python helper or automated test suite. The workflow is manual: users install the templates, review Git status in their client, and decide which project files to stage and commit.

## Template policy
- Ignore common generated Unity cache folders rooted at the project (`Library`, `Temp`, `Obj`, `Logs`, `UserSettings`), root `Build` and `Builds` output folders, root `.vscode`, and operating-system metadata. Under root `Thry`, ignore only `/Thry/preset_cache.txt`, `/Thry/presets_known_materials.txt`, and `/Thry/trash/`; keep other Thry configuration and persistent data visible. Keep captures, recordings, and archives visible by default; optional commented examples for captures and recordings are inactive.
- Keep `Assets/`, `ProjectSettings/`, archives, captures, recordings, and other project files visible by default. Under root `Packages/`, keep only `manifest.json`, `packages-lock.json`, and `vpm-manifest.json` visible; ignore all other contents, including resolver data and embedded/vendor package source. Explain that users who want a local or embedded package not represented by the manifests must add explicit project-specific exceptions. Ignore patterns do not untrack files already committed.
- Preserve Unity `.meta` files alongside their assets. VRChat projects can use VCC to restore declared VPM dependencies using the kept manifests; do not claim the shared template keeps resolver or package payload files.
- `.gitattributes` routes common binary media extensions and `.unitypackage` files through Git LFS regardless of size. Text and Unity YAML stay in regular Git. Unusual binary Unity serialized files require an explicit, reviewable LFS pattern added by the project owner; never route Unity YAML or `.meta` files through LFS.
- GitHub rejects regular Git blobs larger than 100 MiB. Git LFS stores payloads separately and may have account or organization storage and bandwidth limits.

## Maintenance
- Update the templates, README, and this file together when shared ignore or LFS policy changes; keep README guidance accurate and avoid claims that defaults fit every project.
- Review ignore behavior and attributes using a disposable Unity-shaped Git repository when a template change could hide or misclassify project files. Check representative Assets and `.meta` files, ProjectSettings, the three visible package manifests and ignored package contents, the three excluded Thry paths and visible Thry configuration, `.vscode`, generated folders, and LFS-matched and ordinary text files. Keep this repository itself out of any avatar-specific workflow.
