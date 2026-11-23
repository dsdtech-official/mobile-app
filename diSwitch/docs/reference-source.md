<!-- SPDX-FileCopyrightText: 2026 DongGuan DESHIDE TECHNOLOGY CO., LTD (DSD TECH) -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->
# diSwitch Android 2.4 reference source

An adapted historical reference snapshot based on **DSD TECH SWITCH Android
2.4 (versionCode 6)**, now named diSwitch. It is **not a byte-for-byte copy of
the original 2.4 release source**, not the source of the current store app,
and does not include iOS source or an installable APK/AAB.

## Availability

The reference source has not yet been published. Use the
[store downloads](../README.md#downloads) for normal installation.

The source package is separate from this documentation repository. GitHub's
automatic **Source code (zip/tar.gz)** archives of this repository contain the
documentation, not the separately packaged Android application source.

## Snapshot contents and changes

The 148-file snapshot includes the production `app` module, bundled
`FastBleLib` source, Gradle Wrapper and build configuration, resources,
English documentation and license notices. Tests, private development history,
local SDK paths, original signing material and generated build outputs are
excluded. The application ID remains `com.reb.switchbt`.

The password-entry and password-setting interface has been independently
reimplemented using native Android controls. The former password component,
duplicate legacy password implementation and unused legacy resources were
removed. The historical BLE commands and data format are retained. These
changes do not establish functional equivalence on physical hardware.

## Build and validation limits

See `README.md` inside the source package for build prerequisites and commands.
The verified environment used **JDK 25, Android SDK 37 and existing dependency
caches**. Debug and unsigned Release builds and Debug Lint completed; Debug
Lint reported **0 errors and 147 warnings**.

A separate validation copy ran **122 host regression tests**, with no failures,
errors or skipped tests. The distributed snapshot itself contains no tests.
The 148 production inputs used for the application-only build matched the
snapshot. These results do not establish a fresh-machine dependency download,
physical S22/BLE operation or manual accessibility verification of this adapted
2.4 snapshot. No such device validation was performed for this snapshot.

Use your own signing identity for distribution. A differently signed build
cannot replace the installed store app while retaining its signing identity.

## Licenses, attribution and graphics

The Apache-2.0 license applies only to original code DSD TECH is entitled to
license. Read `LICENSE`, `THIRD_PARTY_NOTICES.md` and `licenses/` inside the ZIP;
third-party notices and historical copyright attribution remain attached.

FastBle retains its upstream Apache-2.0 license and author attribution. Its
source was compared with upstream 2.3.2; the exact historical import revision
has not been independently established. Modification notices identify the
changed files. Gradle Wrapper license information is retained and its
checksum and the distribution checksum are documented in the package.

Of the 39 PNG files, six copies of `logo.png` and `ic_launcher.png` are company
brand assets. The other 33 PNGs, covering nine legacy image names, retain
**unidentified original authors and redistribution terms**. Their retention
does not establish permission to redistribute them or place them under
Apache-2.0. The full list is in `THIRD_PARTY_NOTICES.md`; do not treat every
file in this package as Apache-2.0 licensed. No additional trademark rights
are granted.

[Back to diSwitch](../README.md) · [All mobile apps](../../README.md)
