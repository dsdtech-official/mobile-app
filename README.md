<!-- SPDX-FileCopyrightText: 2026 DongGuan DESHIDE TECHNOLOGY CO., LTD (DSD TECH) -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
# DSD TECH mobile apps

Download DSD TECH mobile apps, find usage guides and protocol references,
and get help with supported devices.

## Choose your app

| App | Main use | Platforms | Store downloads |
|---|---|---|---|
| [diBlue](diBlue/README.md) | BLE data terminal and supported relay control | Android, iOS | [Google Play](https://play.google.com/store/apps/details?id=com.reb.dsd_ble) · [App Store](https://apps.apple.com/app/id1441528159) |
| [diSwitch](diSwitch/README.md) | Compatible Bluetooth relay control | Android, iOS | [Google Play](https://play.google.com/store/apps/details?id=com.reb.switchbt) · [App Store](https://apps.apple.com/app/id1483733224) |
| [diSPP](diSPP/README.md) | Classic Bluetooth SPP serial terminal | Android | [Google Play](https://play.google.com/store/apps/details?id=com.reb.dsd_spp) |

- For BLE data communication, see [diBlue](diBlue/README.md).
- For classic Bluetooth SPP communication, see [diSPP](diSPP/README.md).
- For relay control, compare the hardware and platform requirements on the
  [diBlue](diBlue/README.md) and [diSwitch](diSwitch/README.md) pages.

## Guides and protocols

- **diBlue:** [BLE data connection](diBlue/docs/bluetooth-data-connection.md)
  and [Bluetooth relay protocol](diBlue/docs/bluetooth-relay-protocol.md).
- **diSwitch:** [App features, compatibility and device management](diSwitch/README.md).
- **diSPP:** [Text / HEX communication, commands and compatibility](diSPP/README.md).

Each app has its own directory. Its README contains app information and
support links; detailed guides and protocol references belong in that app's
`docs/` directory when available. Protocol applicability is defined by each
document's hardware and firmware scope.

## Help and feedback

| App | Report a problem | Suggest an improvement |
|---|---|---|
| diBlue | [Problem report](https://github.com/dsdtech-official/mobile-app/issues/new?template=diblue-bug.yml) | [Suggestion](https://github.com/dsdtech-official/mobile-app/issues/new?template=diblue-feature.yml) |
| diSwitch | [Problem report](https://github.com/dsdtech-official/mobile-app/issues/new?template=diswitch-bug.yml) | [Suggestion](https://github.com/dsdtech-official/mobile-app/issues/new?template=diswitch-feature.yml) |
| diSPP | [Problem report](https://github.com/dsdtech-official/mobile-app/issues/new?template=dispp-bug.yml) | [Suggestion](https://github.com/dsdtech-official/mobile-app/issues/new?template=dispp-feature.yml) |

GitHub feedback requires an account and is public. Remove passwords, personal
information, device identifiers, order details and sensitive communication data
from reports and attachments. For private support or if you cannot use GitHub,
[email DSD TECH](mailto:dsd_tech@outlook.com).

## Historical source and licensing

This repository contains documentation and feedback forms. Install the apps
through their store links above. The [diBlue historical source page](diBlue/docs/reference-source.md)
provides older Android and iOS reference archives, their Release links,
licenses and validation limits. Those archives are **not the current store
apps' source code**. The iOS reference revision has not been rebuilt with Xcode.

A separate [diSwitch Android 2.4 reference snapshot](diSwitch/docs/reference-source.md)
is being prepared for publication. It is an adapted historical snapshot,
not the original release source or current store source; see its validation
limits and third-party graphics notices.

Documentation and feedback templates are licensed under
[CC BY-SA 4.0](LICENSES/CC-BY-SA-4.0.txt), except that the
[diBlue relay protocol](diBlue/docs/bluetooth-relay-protocol.md) and
[BLE data connection guide](diBlue/docs/bluetooth-data-connection.md), including
their examples, use [Apache-2.0](LICENSES/Apache-2.0.txt).
These documentation licenses do not grant rights to the applications,
their separately distributed source archives or third-party components.
