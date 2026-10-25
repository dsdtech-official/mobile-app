<!-- SPDX-FileCopyrightText: 2026 DongGuan DESHIDE TECHNOLOGY CO., LTD (DSD TECH) -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
# diBlue

diBlue, formerly **DSD TECH Bluetooth**, is a Bluetooth Low Energy (BLE) terminal
for compatible devices and supported DSD TECH relay modules. It is available
for Android and iOS.

## Downloads

For normal use, install diBlue from the store for your device:

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

The [official download page](https://www.deshide.com/News-detail_DSDTechBluetooth.html)
also identifies the app by its former name, DSD TECH Bluetooth.

## Usage guides

| What you need | Guide |
|---|---|
| Connect a BLE module and send or receive Text / HEX data | [Bluetooth Module Data Connection](docs/bluetooth-data-connection.md) — default UUIDs, subscription, byte encoding and transfer limits; module examples include HM-10, HM-11, HM-18 and HM-20. |
| Control a compatible relay or implement your own client | [Bluetooth Relay Protocol](docs/bluetooth-relay-protocol.md) — compatible models, A1.1 / A1.2 capabilities, packets and A1.2 programming examples. |

These guides are independent of the historical source snapshots below.
They do not imply that those snapshots implement all current features,
including newer relay state-query or detection behavior. Model names alone
do not establish a module's GATT configuration.

## Help and feedback

- [Report a problem](https://github.com/dsdtech-official/mobile-app/issues/new?template=diblue-bug.yml)
- [Suggest an improvement](https://github.com/dsdtech-official/mobile-app/issues/new?template=diblue-feature.yml)
- Prefer private support or cannot use GitHub? [Email DSD TECH](mailto:dsd_tech@outlook.com).

For a problem report, include your platform and app version, whether you use
the store app or a historical-source build, phone/tablet model, OS version,
related hardware, steps to reproduce, and expected / actual results.
Enter `unknown` if you cannot find the app version. Add screenshots or logs
only when useful. For a suggestion, explain what you want to do and how it
would help.

**GitHub feedback requires an account and is public.** Remove passwords,
account details, device identifiers, order details and sensitive communication
data from reports, logs and screenshots. Send private support details by email.

## Android features and compatibility

- Discover nearby BLE devices, save favorites and assign local device aliases.
- Send and receive Text / HEX once or repeatedly at a chosen interval; choose
  text line endings: None, CR, LF or CRLF.
- Reuse command history and starred commands. Selecting a saved command fills
  the input for review rather than sending it automatically.
- Detect supported relay channel counts, refresh reported states and control
  individual channels or all channels together.
- Choose nine interface languages; adjust log timestamps, automatic scrolling
  and whether the screen stays on while connected.

These features describe the newer Android app, not the historical 2.5.1
snapshot. They are not a feature specification for iOS.

The Android app requires compatible BLE hardware and GATT services and
characteristics. Relay control requires a supported relay protocol.
**Classic Bluetooth SPP-only connections are not supported.** The app does not
work with every Bluetooth device.

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

## Privacy

The [diBlue iOS privacy policy](https://github.com/dsdtech-official/.github/blob/main/docs/diblue/PRIVACY.md)
covers the iOS app. It does not cover the Android app.

[All mobile apps](../README.md)
