<!-- SPDX-FileCopyrightText: 2026 DongGuan DESHIDE TECHNOLOGY CO., LTD (DSD TECH) -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
# diSPP

diSPP, formerly **DSD TECH SPP**, is an Android Bluetooth serial terminal by
DSD TECH for devices that support **classic Bluetooth SPP**. Use it to send
commands, inspect received data and manage the devices you work with.

## Downloads

| Platform | App download |
|---|---|
| Android | [Google Play](https://play.google.com/store/apps/details?id=com.reb.dsd_spp) |

Install the store app for normal use.

## Send and receive

- View received data as text or hexadecimal bytes.
- Send UTF-8 text or hexadecimal data.
- Choose no line ending, CR, LF or CRLF for text commands.
- Repeat a command at a chosen interval and stop it when needed.

A successful send means the data was written to the Bluetooth connection;
it does **not** confirm that the remote device executed the command.

## Reuse your commands

- Restore successfully sent commands from history without sending them
  immediately.
- Keep frequently used commands as favorites and pin entries for quick access.
- Review a command before sending it to the connected device.

## Organize devices

- Scan for nearby devices and keep saved devices in **My devices**.
- Set local aliases to recognize devices in the list and Data header.
- Mark unrelated devices to hide them from the nearby list.
- Manage saved unrelated marks even when the device is absent from the current
  scan. Removing a mark does not automatically add or connect the device.

Pairing, adding a device to **My devices** and connecting are separate actions.

## Display options

- Turn receive timestamps and automatic scrolling on or off.
- Keep the screen awake while the connected communication page is in the
  foreground.
- View scan signal strength when a current sample is available.

## Compatibility and permissions

The connected device must support **classic Bluetooth SPP**.
**BLE-only devices are not supported.**

Bluetooth permissions are required. Older Android versions may also require
location permission for scanning.

The current app uses a general Data page for communication. The dedicated
relay-control page from older versions has been removed.

## Documentation

See the [documentation index](docs/README.md) for app-specific resources.

## Help and feedback

- [Report a problem](https://github.com/dsdtech-official/mobile-app/issues/new?title=%5BdiSPP%5D%5BProblem%5D%3A%20)
- [Suggest an improvement](https://github.com/dsdtech-official/mobile-app/issues/new?title=%5BdiSPP%5D%5BSuggestion%5D%3A%20)
- Prefer private support or cannot use GitHub? [Email DSD TECH](mailto:dsd_tech@outlook.com).

For a problem report, include your app version, phone or tablet model, Android
version, related Bluetooth device model, steps to reproduce, and expected /
actual results. Enter `unknown` if you cannot find the app version. For a
suggestion, explain what you want to do and how it would help.

**GitHub feedback requires an account and is public.** Remove personal
information, passwords, device identifiers, order details and sensitive
communication data from reports, logs and screenshots. Send private support
details by email.

## Local data and privacy

Aliases, command history and settings are stored locally by the app.
Read the [Android app privacy policy](https://www.deshide.com/News-detail_3032263.html).

[All mobile apps](../README.md)
