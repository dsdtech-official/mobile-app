<!-- SPDX-FileCopyrightText: 2026 DongGuan DESHIDE TECHNOLOGY CO., LTD (DSD TECH) -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
# diBlue historical reference source

These archives contain older DSD TECH Bluetooth application code, provided for
reference only. They are **not the source code of the current diBlue store apps**
and are not installable APKs or IPAs. For normal use, install the store app from
[diBlue downloads](../README.md#downloads).

## Reference downloads

| Platform | App download | Historical source — reference only |
|---|---|---|
| Android | [Google Play](https://play.google.com/store/apps/details?id=com.reb.dsd_ble) | [DSD TECH Bluetooth 2.5.1 ZIP](https://github.com/dsdtech-official/mobile-app/releases/download/diBlue/android-v2.5.1/diBlue-android-v2.5.1-reference-source.zip) · [Release notes](https://github.com/dsdtech-official/mobile-app/releases/tag/diBlue/android-v2.5.1) |
| iOS | [App Store](https://apps.apple.com/app/id1441528159) | [DSD TECH Bluetooth 2.3 ZIP](https://github.com/dsdtech-official/mobile-app/releases/download/diBlue/ios-v2.3/diBlue-ios-v2.3-reference-source.zip) · [Release notes](https://github.com/dsdtech-official/mobile-app/releases/tag/diBlue/ios-v2.3) |

> **The source ZIPs are old versions provided for reference only, not the source
> code of the current diBlue store apps. They are not installable APKs or IPAs.**
> **The iOS reference revision has not been rebuilt with Xcode.**

Download the named source ZIPs in the table. GitHub's automatic **Source code
(zip/tar.gz)** downloads contain this documentation repository, not the
separately attached Android or iOS application source. The main branch contains
documentation and feedback forms only.

## Historical Android source: DSD TECH Bluetooth 2.5.1

> **Old-version reference code only:** this ZIP contains the historical
> **DSD TECH Bluetooth 2.5.1** Android codebase (versionCode **10**).
> It is **not the source code of the current diBlue store app** and does not
> contain iOS source code.

<details>
<summary>Archive contents, version differences, licenses and build limitations</summary>

The archive contains 151 files: application sources and resources, Gradle build
files and Wrapper, documentation and license notices. Tests, test-only build
settings, generated caches, original signing material and installation packages
are excluded. The archive is not a ready-to-install APK or AAB.

Version 2.5.1 predates the newer device favorites and aliases, command history,
nine-language interface and relay detection/state-refresh features.
Its original app name and interface may still say DSD TECH Bluetooth.
Use the store app for normal use; the historical snapshot is intended for
reference and does not establish compatibility with your current app or device.

The archive includes an Apache-2.0 license for code the owner is entitled to
license. Third-party files retain their own notices and terms, including the
Nordic attribution and supplied BSD license. Read `LICENSE`,
`THIRD_PARTY_NOTICES.md` and `licenses/` inside the ZIP; do not treat every file
as Apache-2.0 licensed.

The final application-only project compiled using an existing local toolchain
and dependency cache. This was not a fresh-environment build, complete test
suite, APK validation or hardware verification. No tests are distributed in
the reference ZIP.

</details>

## Historical iOS source: DSD TECH Bluetooth 2.3

> **Old-version reference code only:** this ZIP contains the historical
> **DSD TECH Bluetooth 2.3** iOS Objective-C codebase (build **4**).
> It is **not the source code of the current diBlue store app** or the newer
> diBlue Swift app. It does not include Android source or an IPA.

**This English, application-only revision has received static checks only
and has not been rebuilt with Xcode. No runtime or hardware validation is
claimed for this revision.**

<details>
<summary>Archive contents, licenses and build limitations</summary>

The iOS ZIP contains 179 files: application source and resources, the
`TechBluetooth.xcodeproj` project and shared scheme, documentation and licenses.
Legacy template tests and their project targets, signing material, generated
build output and private development history are excluded. The main branch
continues to contain documentation and feedback forms only.

Comments, diagnostic messages, UI labels and Bluetooth permission text have
been translated into English. The project uses an example bundle identifier;
choose your own identifier and development team for a device build. The code
license does not grant rights to use DSD TECH branding for your own product.

**This English, application-only revision has received static checks only and
has not been rebuilt with Xcode.** An earlier revision, before the translation
and test removal, completed an unsigned Debug simulator build on a Mac with
an iOS 15.0 deployment-target override. That result does not establish a
successful build of this revision, historical iOS 9.3 compatibility, App Store
eligibility or real BLE/relay behavior. No fresh-environment build, runtime
or hardware validation is claimed for this revision.

Project-owned code is licensed under Apache-2.0. Vendored Masonry and
MBProgressHUD retain their original notices and MIT terms; their exact
historical import revisions have not been independently identified. Read
`LICENSE`, `NOTICE`, `THIRD_PARTY_NOTICES.md` and `LICENSES/` inside the ZIP.

</details>

[Back to diBlue](../README.md) · [All mobile apps](../../README.md)
