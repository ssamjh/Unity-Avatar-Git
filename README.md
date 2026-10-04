# Git configuration for Unity and VRChat projects

This repository provides reusable `.gitignore` and `.gitattributes` templates. Copy `templates/.gitignore` and `templates/.gitattributes` into the root of a Unity project. The root `.gitignore` and `.gitattributes` in this repository apply only to this template repository.

If the Unity project does not already use Git, initialize a repository in its root. With Git LFS installed, run `git lfs install --local` there. Then review the project in your Git client and choose which files to stage and commit.

## What the templates do

The ignore template excludes the Unity cache and local-data folders `/Library`, `/Temp`, `/Obj`, `/Logs`, and `/UserSettings`, root `/Build` and `/Builds` output folders, root `/.vscode/`, generated root project files, other IDE caches, and operating-system metadata. Under `/Thry/`, it excludes only `/Thry/preset_cache.txt`, `/Thry/presets_known_materials.txt`, and `/Thry/trash/`; other Thry configuration and persistent data remain visible. In `/Packages/`, only the root `manifest.json`, `packages-lock.json`, and `vpm-manifest.json` are kept visible by default; package payloads, resolver data, and embedded package source are ignored. `Assets/`, `ProjectSettings/`, archives, captures, recordings, and other project files remain visible. Optional commented rules show how to exclude capture and recording folders if you choose. Keep Unity `.meta` files alongside their assets.

The attributes template routes common binary media extensions and `.unitypackage` files through Git LFS, regardless of size. Unity text and YAML files remain in regular Git. It cannot identify every unusual binary Unity serialized file; add a visible, specific LFS rule for any such file type or path you use.

Review the ignore rules and Git's status before staging. If you need to include a local or embedded package that is not represented by a manifest, add explicit project-specific exceptions for that package and its contents to the project's `.gitignore`. Ignore rules do not stop tracking files already committed.

For VRChat projects, VCC can restore declared VPM dependencies from the kept manifests. Package files are not included by default; add explicit exceptions for any local or embedded package content you need in version control.

## Requirements and references

- Git
- Git LFS installed and available as `git lfs`
- VRChat Creator Companion (VCC) when restoring declared VRChat packages

References: [GitHub's Unity ignore template](https://github.com/github/gitignore/blob/main/Unity.gitignore), [VRChat VCC source control guidance](https://vcc.docs.vrchat.com/vpm/source-control/), and [Git LFS documentation](https://git-lfs.com/).
