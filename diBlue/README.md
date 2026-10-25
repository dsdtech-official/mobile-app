<!-- SPDX-FileCopyrightText: 2026 DongGuan DESHIDE TECHNOLOGY CO., LTD (DSD TECH) -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
# diBlue

diBlue, formerly **DSD TECH Bluetooth**, is a Bluetooth Low Energy (BLE) terminal
for compatible devices and supported DSD TECH relay modules. It is available
for Android and iOS.

## Install the app

For normal use, install diBlue from the store for your device:

| Platform | Download |
|---|---|
| Android | [Google Play](https://play.google.com/store/apps/details?id=com.reb.dsd_ble) |
| iOS | [App Store](https://apps.apple.com/app/id1441528159) |

The [official download page](https://www.deshide.com/News-detail_DSDTechBluetooth.html)
also identifies the app by its former name, DSD TECH Bluetooth.

## Android app highlights

- Discover nearby BLE devices, save favorites and assign local device aliases.
- Send and receive text or HEX data, once or repeatedly at a chosen interval.
- Choose text line endings: None, CR, LF or CRLF.
- Reuse command history and starred commands. Selecting a saved command fills
  the input for review rather than sending it automatically.
- Detect supported relay channel counts, refresh reported states and control
  individual channels or all channels together.
- Choose from nine interface languages and adjust log timestamps, automatic
  scrolling and whether the screen stays on while connected.

These highlights describe the newer Android app, not the historical 2.5.1
source snapshot described below. They are not a feature specification for iOS.

The Android app requires compatible BLE hardware and GATT services and
characteristics. Relay control requires a supported relay protocol.
Classic Bluetooth SPP devices are not supported, and the app does not work
with every Bluetooth device.

## Historical Android source: 2.5.1

> **Reference only:** the source ZIP contains the historical Android
> **2.5.1** codebase (versionCode **10**). It is **not the source code of the
> latest store version**, and it does not contain the iOS source code.

The historical source is available in the
[diBlue Android 2.5.1 Release](https://github.com/dsdtech-official/mobile-app/releases/tag/diBlue/android-v2.5.1).
Download the attached
[reference source ZIP](https://github.com/dsdtech-official/mobile-app/releases/download/diBlue/android-v2.5.1/diBlue-android-v2.5.1-reference-source.zip)
(`diBlue-android-v2.5.1-reference-source.zip`).
The main branch contains documentation and feedback forms only; it does not
contain the Android application source.

The archive contains 151 files: application sources and resources, Gradle build
files and Wrapper, documentation and license notices. Tests, test-only build
settings, generated caches, original signing material and installation packages
are excluded. The archive is not a ready-to-install APK or AAB.

Use the specifically attached reference source ZIP. GitHub's automatically generated **Source code (zip)** and
**Source code (tar.gz)** archives contain this documentation repository, not
the separately attached Android application source.

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

## Historical iOS source: 2.3

> **Reference only:** this historical Objective-C snapshot is **iOS 2.3
> (build 4)**. It is **not the source code of the latest store version** or
> the newer diBlue Swift app. It does not include Android source or an IPA.

The iOS reference source is prepared for a separate versioned Release as
`diBlue-ios-v2.3-reference-source.zip`. No iOS source download has been published
yet; check [Releases](../../../releases) after publication. The Android 2.5.1
ZIP linked above is a different platform and version.

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
Use the specifically attached iOS source ZIP when available: GitHub's automatic
**Source code (zip/tar.gz)** downloads contain this documentation repository.

## Report a problem

Open [Issues](../../../issues), select **diBlue: Report a problem**, and include:

- Android or iOS, and the diBlue version you are using. Enter `unknown` if needed.
- Whether you are using the store app or a build from the historical reference source.
- Your phone or tablet model and operating system version.
- Related hardware, if applicable.
- The steps you followed, what you expected, and what actually happened.
- Screenshots or logs, if useful, with sensitive information removed.

## Suggest an improvement

Open [Issues](../../../issues) and choose **diBlue: Suggest an improvement**.
Describe what you want to do, which platform you use, and how the change would
help.

## Before posting

You need a GitHub account to submit feedback. Reports and comments are public.
Do not include passwords, account details, device identifiers, order details,
or sensitive communication data.

If you cannot use GitHub, contact [DSD TECH support](mailto:dsd_tech@outlook.com).
Do not post private support details in a public issue.

## Privacy

The [diBlue iOS privacy policy](https://github.com/dsdtech-official/.github/blob/main/docs/diblue/PRIVACY.md)
covers the iOS app. It does not cover the Android app.

[All mobile apps](../README.md)
