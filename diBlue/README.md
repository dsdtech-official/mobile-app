<!-- SPDX-FileCopyrightText: 2026 DongGuan DESHIDE TECHNOLOGY CO., LTD (DSD TECH) -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
# diBlue

diBlue, formerly **DSD TECH Bluetooth**, is a Bluetooth Low Energy (BLE) terminal
for compatible devices and supported DSD TECH relay modules. It is available
for Android and iOS.

## Downloads

| Platform | App download |
|---|---|
| Android | [Google Play](https://play.google.com/store/apps/details?id=com.reb.dsd_ble) |
| iOS | [App Store](https://apps.apple.com/app/id1441528159) |

Install the store app for normal use. The [official download page](https://www.deshide.com/News-detail_DSDTechBluetooth.html)
also identifies the app by its former name, DSD TECH Bluetooth.

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

## Usage guides

| What you need | Guide |
|---|---|
| Connect a BLE module and send or receive Text / HEX data | [Bluetooth Module Data Connection](docs/bluetooth-data-connection.md) — default UUIDs, subscription, byte encoding and transfer limits; module examples include HM-10, HM-11, HM-18 and HM-20. |
| Control a compatible relay or implement your own client | [Bluetooth Relay Protocol](docs/bluetooth-relay-protocol.md) — compatible models, A1.1 / A1.2 capabilities, packets and A1.2 programming examples. |

These guides are independent of the historical source snapshots.
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

## Privacy

The [diBlue iOS privacy policy](https://github.com/dsdtech-official/.github/blob/main/docs/diblue/PRIVACY.md)
covers the iOS app. It does not cover the Android app.

## Historical reference source

The [historical source archives](docs/reference-source.md) are old versions for
reference only, **not the source code of the current diBlue store apps** and
not installable APKs or IPAs. The iOS reference revision has not been rebuilt
with Xcode. See the archive page for licenses and build limitations.

## Historical Android source: DSD TECH Bluetooth 2.5.1

[Android reference source, downloads, licenses and validation limits](docs/reference-source.md#historical-android-source-dsd-tech-bluetooth-251).

## Historical iOS source: DSD TECH Bluetooth 2.3

[iOS reference source, downloads, licenses and validation limits](docs/reference-source.md#historical-ios-source-dsd-tech-bluetooth-23).

[All mobile apps](../README.md)
