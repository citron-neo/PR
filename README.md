# 🍋 Citron Neo PR Builds

[![Build Citron Neo (Android)](https://github.com/citron-neo/CI/actions/workflows/build-android.yml/badge.svg)](https://github.com/citron-neo/CI/actions/workflows/build-android.yml) [![Build Citron Neo (Windows)](https://github.com/citron-neo/CI/actions/workflows/build-windows.yml/badge.svg)](https://github.com/citron-neo/CI/actions/workflows/build-windows.yml) [![Build Citron Neo (Linux)](https://github.com/citron-neo/CI/actions/workflows/build-linux.yml/badge.svg)](https://github.com/citron-neo/CI/actions/workflows/build-linux.yml) [![Build Citron Neo (macOS)](https://github.com/citron-neo/CI/actions/workflows/build-macos.yml/badge.svg)](https://github.com/citron-neo/CI/actions/workflows/build-macos.yml)

---

This repository builds **on-demand test artifacts for open pull requests** against the Citron Neo emulator — it does **not** produce the project's Nightly or Stable releases. For those, see [citron-neo/CI](https://github.com/citron-neo/CI).

Each platform workflow (Windows, Linux, Android, macOS) is triggered manually via `workflow_dispatch`, taking a target branch, a PR number, and a head repo as input. This lets a reviewer or contributor build a specific PR's branch — from any fork — without waiting for it to merge.

Once a build is requested, this repository:

- Builds the requested commit for the chosen platform.
- Posts (or updates) a single results comment on the corresponding pull request in [citron-neo/emulator](https://github.com/citron-neo/emulator), with a table tracking each platform's status (`Pending` → `Building...` → `Success`/`Failed`) and a direct download link to the artifact, powered by [nightly.link](https://nightly.link).
- Skips rebuilding a commit that's already been built successfully for that platform, to avoid duplicate work on repeated dispatches.

Would you like to submit a compatibility report for the emulator? You can do so here:

- [Submit Compatibility Report](https://github.com/citron-neo/Citron-Compatability)

---

Direct links for other information you may need can also be found below:

- [Latest Commits Can Be Found Here](https://github.com/citron-neo/emulator/commits/main)
- [citron-neo/CI — Nightly & Stable Releases](https://github.com/citron-neo/CI)
- [citron-neo/emulator — Open Pull Requests](https://github.com/citron-neo/emulator/pulls)

---

# READ THIS IF YOU HAVE ISSUES

If you are on wayland (specially GNOME wayland) and get freezes or crashes, you are likely affected by this issue that affects all Qt6 apps: [citron-neo/CI#50](https://github.com/citron-neo/CI/pull/50)

To fix it simply set the env variable `QT_QPA_PLATFORM=xcb`

**Also, are you looking for AppImages of other emulators? Check:** [AnyLinux-AppImages](https://pkgforge-dev.github.io/Anylinux-AppImages/)

---

Linux AppImage builds are made using [sharun](https://github.com/VHSgunzo/sharun), which makes it extremely easy to turn any binary into a portable package without using containers or similar tricks.

**These AppImages bundle everything and should work on any Linux distro, even on musl based ones.**

A `tar.zst` portable archive of the same build is also produced alongside the AppImage, for users who prefer an install-free tarball over the AppImage format.

These AppImages work without fuse2 as they can use fuse3 instead; they can also work without fuse at all thanks to the [uruntime](https://github.com/VHSgunzo/uruntime).

---

Thank-you for being a part of & using Citron Neo, we value all members of the community whom help shape the emulator into what it is today!

- The Citron Neo Team
