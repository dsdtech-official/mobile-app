<!-- SPDX-FileCopyrightText: 2026 DongGuan DESHIDE  TECHNOLOGY CO.,LTD -->
<!-- SPDX-License-Identifier: Apache-2.0 -->
# Bluetooth Relay Protocol

A compact reference for compatible DSD TECH BLE relays with **A1.1** or **A1.2** firmware. This protocol is independent of the programming language or operating system. It is not a general protocol for every Bluetooth relay.

## 1. Compatible models and firmware

Compatible models: **SH-BT01A**, **SH-BT01E**, **SH-BT02A**, **SH-BT04A**.

The control workflow and programming examples below target **A1.2**, the firmware used in current products. A1.1 is documented only for historical compatibility.

| Capability | A1.1 — legacy | A1.2 — current |
| --- | --- | --- |
| Product status | Pre-2023 firmware; no longer sold or shipped, but still in use | Firmware used in currently sold relays |
| Channel configurations | 1, 2 or 4 | 1, 2 or 4 |
| ON / OFF commands | Supported | Same commands as A1.1 |
| State queries | Not supported | Supported |
| State confirmation | No query-based confirmation | Explicit query returns the reported state |
| Channel count | Configure manually | Configure manually or use optional probing |

The labels describe firmware capabilities; the packets below do not provide a firmware-version read command. A missing reply alone cannot identify firmware or prove that a channel does not exist. No specific A1.2 introduction date is implied.

## 2. BLE connection and byte encoding

Use BLE GATT, not Classic Bluetooth SPP. Default identifiers:

| Purpose | UUID |
| --- | --- |
| Service | `0000ffe0-0000-1000-8000-00805f9b34fb` |
| Write characteristic | `0000ffe1-0000-1000-8000-00805f9b34fb` |
| Notify characteristic | `0000ffe1-0000-1000-8000-00805f9b34fb` |
| CCCD | `00002902-0000-1000-8000-00805f9b34fb` |

Connect, discover the service / characteristics, and enable notifications before querying. The reference client uses Write Without Response; use the characteristic's advertised properties and your BLE library's API. Subscribe through the BLE library; enable indications instead if that is the available characteristic property.

**Send four raw bytes**, not ASCII text containing hexadecimal digits. Do not append CR, LF, a terminator or a length prefix. For example, `A0 01 01 A2` means bytes `0xA0, 0x01, 0x01, 0xA2`.

## 3. Packet format

All numbers below are hexadecimal. Each packet is exactly four bytes. `c` is the channel `01`–`04`; `s` is `00` (OFF) or `01` (ON). Use only channels present on the device. Device configurations are 1, 2 or 4 consecutive channels, starting at 1.

| Packet | Byte 0 | Byte 1 | Byte 2 | Byte 3: checksum |
| --- | --- | --- | --- | --- |
| Control: host → relay | `A0` | `c` | `s` | `(0xA0 + c + s) & 0xFF` |
| Query: host → A1.2 relay | `A1` | `c` | `FF` | `(0xA1 + c) & 0xFF` |
| State: A1.2 relay → host | `A1` | `c` | `s` | `(0xA0 + c + s) & 0xFF` |

**Do not sum the first three bytes for query or reply checksums.** In particular, the state reply starts with `A1`, but its checksum uses `A0 + c + s`.

| Channel | ON | OFF | Query (A1.2) | Reply: ON | Reply: OFF |
| --- | --- | --- | --- | --- | --- |
| 1 | `A0 01 01 A2` | `A0 01 00 A1` | `A1 01 FF A2` | `A1 01 01 A2` | `A1 01 00 A1` |
| 2 | `A0 02 01 A3` | `A0 02 00 A2` | `A1 02 FF A3` | `A1 02 01 A3` | `A1 02 00 A2` |
| 3 | `A0 03 01 A4` | `A0 03 00 A3` | `A1 03 FF A4` | `A1 03 01 A4` | `A1 03 00 A3` |
| 4 | `A0 04 01 A5` | `A0 04 00 A4` | `A1 04 FF A5` | `A1 04 01 A5` | `A1 04 00 A4` |

There is no dedicated ALL ON / ALL OFF packet. Send one control packet per installed channel.

## 4. A1.2 control workflow

 Send the control packet, allow the relay to process it, then explicitly query that channel. Accept only a valid reply for the expected channel. Show the returned state, even if it differs from the requested target. Do not rely on an unsolicited control acknowledgement or notification.

Example: switch channel 1 ON and read its state:

```text
Host → Relay: A0 01 01 A2    Control ON
Host → Relay: A1 01 FF A2    Query
Relay → Host: A1 01 01 A2    Reported ON
Alternative: A1 01 00 A1    Reported OFF; target was not confirmed
```

For ALL operations, send all selected control packets first, then query states on A1.2. A query timeout must not prevent the remaining control packets from being sent. On a real control-write failure or disconnection, stop unsent controls and report partial completion; do not automatically replay or reverse them.

## 5. Optional client timing and detection

The following values are **diBlue client policies, not firmware-mandated timing or protocol guarantees**:

- Space consecutive control writes by 100 ms after the previous write completes.
- Wait 500 ms after the final control write before starting state queries.
- For normal state queries, wait up to 4 seconds after write completion; retry once on silence. Do not automatically retry control commands.
- If firmware or channel count is known, use that configuration rather than probing on every connection. A1.1 does not need automatic queries.

Optional probing for devices known to have 1, 2 or 4 consecutive channels:

| Step | Client action | Interpretation |
| --- | --- | --- |
| 1 | Query channel 1; 4 s timeout, one retry | Valid reply establishes query support. Silence leaves identity uncertain; offer legacy mode and manual channel count. |
| 2 | After a valid channel-1 reply, query channel 2; 1.5 s, no retry | Reply: continue. Silence: tentatively select 1 channel. |
| 3 | After a valid channel-2 reply, query channel 3; 1.5 s, no retry | Reply: select 4 channels and read channel 4. Silence: tentatively select 2 channels. |
| 4 | Read channel 4 with normal query timing | A timeout does not invalidate the channel-3 evidence for a 4-channel configuration. |

Packet loss can produce an incorrect inference. Provide a manual override. A failed write or disconnection is not evidence of legacy firmware or a lower channel count. Once A1.2 is configured, a later timeout must not silently downgrade it to A1.1.

## 6. A1.2 programming reference (Python)

These helpers build binary packets and decode a stream of notifications. Connect and subscribe using your BLE library, then write the returned `bytes` to the write characteristic. No BLE connection or output control is performed by the helpers themselves.

```python
def _channel(c):
    if type(c) is not int or c not in (1, 2, 3, 4):
        raise ValueError("Channel must be 1..4")


def control(c, on):
    _channel(c)
    if not isinstance(on, bool):
        raise ValueError("on must be True or False")
    s = int(on)
    return bytes((0xA0, c, s, (0xA0 + c + s) & 0xFF))


def query(c):
    _channel(c)
    return bytes((0xA1, c, 0xFF, (0xA1 + c) & 0xFF))


class ReplyDecoder:
    def __init__(self):
        self.buffer = bytearray()

    def feed(self, data):
        replies = []
        for value in data:
            if not self.buffer and value != 0xA1:
                continue
            self.buffer.append(value)
            if len(self.buffer) < 4:
                continue
            _, c, s, check = self.buffer
            if (c in (1, 2, 3, 4) and s in (0, 1)
                    and check == ((0xA0 + c + s) & 0xFF)):
                replies.append((c, bool(s)))
                self.buffer.clear()
            else:
                del self.buffer[0]
                while self.buffer and self.buffer[0] != 0xA1:
                    del self.buffer[0]
        return replies


packet = control(1, True)  # A0 01 01 A2
request = query(1)        # A1 01 FF A2; A1.2 only
reported = ReplyDecoder().feed(bytes.fromhex("A1 01 01 A2"))
# reported == [(1, True)]
```

Keep one decoder per connection; pass every notification to `feed()` and reset it on disconnection. Its buffer retains at most three bytes between calls. The caller must match the expected query channel and manage timeout / cancellation; valid decoding alone does not correlate a reply to a request.

## 7. Limitations

- Notifications may contain partial frames or multiple frames; do not assume one notification equals one reply. Reject invalid channels, states and checksums, then resynchronize.
- There is no request identifier. Serialize queries and isolate cancelled / disconnected work locally; an arbitrarily delayed old reply for the same channel cannot be distinguished reliably.
- A1.1 has no query-based state confirmation. A1.2 reports firmware state, not an independent measurement of physical contacts or the connected load.
- Absence of a reply does not prove a device is OFF, legacy, disconnected or missing a channel.
- Packet behavior has physical-device evidence for single- and four-channel devices. Not every firmware / channel / hardware combination, including physical two-channel devices, has been independently exercised. No electrical ratings or wiring specification are defined here.

## 8. Copyright and license

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
