# Boxer — agent instructions

This repository is a maintained fork of [Boxer](https://github.com/alunbestor/Boxer) (DOSBox-based Mac emulator), continued as [MaddTheSane/Boxer](https://github.com/MaddTheSane/Boxer). The app is an Xcode project mixing Objective-C, Swift, AppKit, and Metal. Core emulation comes from the `DOSBox-Staging` git submodule plus vendored frameworks (see `.gitmodules`).

## Mission: Forking Boxer for modern macOS

When helping on this codebase, prioritize work that keeps Boxer viable on **current macOS and Apple Silicon** while preserving behavior for users:

- Prefer fixes that align with current Apple SDKs, Xcode toolchains, and 64-bit/arm64 expectations.
- Remove or replace deprecated APIs with supported equivalents; call out behavior changes and testing needs.
- Respect the existing project layout: `Boxer.xcodeproj`, targets **Boxer**, **Boxer Standalone**, and **Boxer Bundler**, and submodules under `Vendor/` and `DOSBox-Staging/`.
- After changing submodules or vendor code, note required `git submodule update --init --recursive` (see `Readme.md`).
- Match surrounding style (naming, patterns, comment density) and keep diffs focused on the requested change.

Avoid drive-by refactors, new dependencies, or large architectural shifts unless explicitly requested.

## Cursor Cloud specific instructions

Cloud agents run on **Linux** (Ubuntu), not macOS. They **cannot** run Xcode or build this Mac app end-to-end. Treat the cloud environment as useful for:

- Editing and reviewing source, project files, scripts, and documentation.
- Working on `DOSBox-Staging` or other components that can be built or tested on Linux when applicable.
- Preparing changes for a human to validate with **Xcode on a Mac** (`xcodebuild`, GUI schemes, device/runtime checks).

For any change that affects linking, codesigning, notarization, Metal, AppKit windowing, or other macOS-only behavior: state clearly what must be verified locally and do not claim the Linux agent verified a full app build.

When opening pull requests from cloud agents, summarize what was changed, why, and concrete **local** verification steps (e.g. schemes to build, smoke tests).

## License and upstream

The project is GPLv2 (see `LICENSE`). Preserve license headers and attribution when touching upstream-derived files.
