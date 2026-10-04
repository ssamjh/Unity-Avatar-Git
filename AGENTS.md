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
- Ignore common generated Unity cache folders rooted at the project (`Library`, `Temp`, `Obj`, `Logs`, `UserSettings`), root `Build` and `Builds` output folders, generated root IDE files/caches, and operating-system metadata. Keep captures, recordings, and archives visible by default; optional commented examples for captures and recordings are inactive.
- Do not ignore `Assets/`, `Packages/`, `ProjectSettings/`, Thry data, package source, manifests, resolver data, archives, or broad file extensions in the shared template. Users may add exact project-specific ignore paths when they know those files can be restored or regenerated. Explain that ignore patterns do not untrack files already committed.
- Preserve Unity `.meta` files alongside their assets. Keep all package content visible by default, including declared VPM package payloads and embedded/vendor source; users choose their project's package policy. VRChat projects can use VCC to restore declared VPM dependencies.
- `.gitattributes` routes common binary media extensions and `.unitypackage` files through Git LFS regardless of size. Text and Unity YAML stay in regular Git. Unusual binary Unity serialized files require an explicit, reviewable LFS pattern added by the project owner; never route Unity YAML or `.meta` files through LFS.
- GitHub rejects regular Git blobs larger than 100 MiB. Git LFS stores payloads separately and may have account or organization storage and bandwidth limits.

## Maintenance
- Update the templates and this file together when shared ignore or LFS policy changes; keep README guidance accurate and avoid claims that defaults fit every project.
- Review ignore behavior and attributes using a disposable Unity-shaped Git repository when a template change could hide or misclassify project files. Check representative Assets and `.meta` files, ProjectSettings, package manifests and source, Thry data, generated folders, and LFS-matched and ordinary text files. Keep this repository itself out of any avatar-specific workflow.
