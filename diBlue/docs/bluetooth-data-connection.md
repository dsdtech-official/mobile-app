<!-- SPDX-FileCopyrightText: 2026 DongGuan DESHIDE  TECHNOLOGY CO.,LTD -->
<!-- SPDX-License-Identifier: Apache-2.0 -->
# Bluetooth Module Data Connection

The **Data** page in diBlue supports the BLE data channel of DSD TECH Bluetooth modules, including **HM-10**, **HM-11**, **HM-18** and **HM-20**. It provides byte-oriented data transfer rather than the dedicated relay controls described in [Bluetooth Relay Protocol](bluetooth-relay-protocol.md).

## 1. Compatibility

Use a module's **BLE GATT** connection. Classic Bluetooth SPP-only connections are not supported. A dual-mode module must expose a compatible BLE data service; the presence of an SPP connection or a Bluetooth device name alone is not sufficient.

The identifiers below are diBlue's defaults. If a module's service or characteristics have been reconfigured, the client must use the identifiers actually exposed by that module. Do not infer the GATT configuration from the model name alone.

## 2. Default BLE identifiers

| Purpose | UUID |
| --- | --- |
| Service | `0000ffe0-0000-1000-8000-00805f9b34fb` |
| Write characteristic: client → module | `0000ffe1-0000-1000-8000-00805f9b34fb` |
| Notify characteristic: module → client | `0000ffe1-0000-1000-8000-00805f9b34fb` |
| CCCD | `00002902-0000-1000-8000-00805f9b34fb` |

The same FFE1 characteristic is used for writing and receiving notifications. diBlue uses **Write Without Response**. Inspect the characteristic properties when implementing another client, and use the BLE library's subscription API to enable notifications; use indications if that is the available property instead.

## 3. Connection sequence

1. Enable Bluetooth and grant the scanning / connection permissions required by the platform.
2. Scan for the module using BLE and connect to its GATT server.
3. Discover the service, write characteristic, receive characteristic and CCCD.
4. Subscribe to notifications and wait for subscription setup to complete.
5. Use the negotiated MTU if available, then start sending data. Do not treat a link-connected event alone as data-ready.

Start with write payloads of at most **20 bytes** unless a larger payload has been negotiated and is supported by the stack / module. For ordinary GATT writes, the ATT payload limit is MTU minus 3. Split longer data into ordered chunks and serialize writes; do not assume a requested MTU is granted.

## 4. Sending and receiving data

- **Text:** diBlue encodes text as UTF-8. The selected line ending is appended once: None, CR (`0D`), LF (`0A`) or CRLF (`0D 0A`). The default is None.
- **HEX:** diBlue converts hexadecimal input into raw bytes. Use complete byte pairs; an odd number of hexadecimal digits is invalid. HEX mode does not append text line endings.
- **Receive:** process the bytes delivered by notifications. Text / HEX display is a client-side representation, not a different BLE transport.

Data mode does not automatically add a packet header, length field, checksum or relay frame. The application or device connected to the module defines the payload format and any acknowledgements.

## 5. Minimal programming example

After connecting and subscribing, pass the resulting bytes to the write characteristic using your BLE library:

```python
SERVICE_UUID = "0000ffe0-0000-1000-8000-00805f9b34fb"
WRITE_UUID = "0000ffe1-0000-1000-8000-00805f9b34fb"
NOTIFY_UUID = WRITE_UUID

text_payload = "HELLO".encode("utf-8")  # 48 45 4C 4C 4F
hex_payload = bytes.fromhex("48 45 4C 4C 4F")  # Same bytes
text_with_crlf = text_payload + b"\r\n"  # Only if the receiver expects CRLF

# Write one selected payload as bytes, not the printed hexadecimal text.
# Deliver incoming notification bytes to your application's receive handler.
```

A notification may contain part of a message or several messages. Use a receive buffer and the receiver's framing rules; UTF-8 characters may also span notifications. Successful BLE writing does not prove that the module's connected device has processed or accepted the command.

Module-specific configuration commands and the connected device's command protocol are separate from this BLE connection procedure.

## 6. Copyright and license

Copyright 2026 DongGuan DESHIDE  TECHNOLOGY CO.,LTD

Brand: DSD TECH.

This document and its code examples are licensed under the Apache License, Version 2.0.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at:

https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, material distributed under
the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF
ANY KIND, either express or implied. See the License for the specific language
governing permissions and limitations under the License.
