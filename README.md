# Git configuration for Unity and VRChat projects

This repository provides reusable `.gitignore` and `.gitattributes` templates. Copy `templates/.gitignore` and `templates/.gitattributes` into the root of a Unity project. The root `.gitignore` and `.gitattributes` in this repository apply only to this template repository.

If the Unity project does not already use Git, initialize a repository in its root. With Git LFS installed, run `git lfs install --local` there. Then review the project in your Git client and choose which files to stage and commit.

## What the templates do

The ignore template excludes the Unity cache and local-data folders `/Library`, `/Temp`, `/Obj`, `/Logs`, and `/UserSettings`, root `/Build` and `/Builds` output folders, generated root project files, IDE caches, and operating-system metadata. It leaves `Assets/`, `Packages/`, `ProjectSettings/`, Thry data, archives, captures, recordings, and other project files visible to Git. Optional commented rules show how to exclude capture and recording folders if you choose. Keep Unity `.meta` files alongside their assets.

The attributes template routes common binary media extensions and `.unitypackage` files through Git LFS, regardless of size. Unity text and YAML files remain in regular Git. It cannot identify every unusual binary Unity serialized file; add a visible, specific LFS rule for any such file type or path you use.

These defaults are intentionally conservative, but each project is different. Review the ignore rules and Git's status before staging. If you know a particular package folder contains only data that your package manager can restore, you may choose to ignore that exact folder by adding a rooted path such as `/Packages/com.vendor.restorable-package/` to the project's `.gitignore`. Do not add broad rules for all of `Packages/` or file extensions that may also match project source. Ignore rules do not stop tracking files already committed.

For VRChat projects, VCC can restore declared VPM dependencies. The templates leave package manifests, resolver data, vendor packages, and embedded package source available for you to include or exclude according to your project's needs.

## Requirements and references

- Git
- Git LFS installed and available as `git lfs`
- VRChat Creator Companion (VCC) when restoring declared VRChat packages

References: [GitHub's Unity ignore template](https://github.com/github/gitignore/blob/main/Unity.gitignore), [VRChat VCC source control guidance](https://vcc.docs.vrchat.com/vpm/source-control/), and [Git LFS documentation](https://git-lfs.com/).
