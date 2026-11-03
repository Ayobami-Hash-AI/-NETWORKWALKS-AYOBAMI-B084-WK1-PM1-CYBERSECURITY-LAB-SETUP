# Week 1 Supplement: Wireshark Traffic Analysis

**Author:** Ayobami Odulaja  
**Programme:** NETWORKWALKS Cybersecurity Internship — Cohort B084  
**Status:** In progress

## Objective
I am extending my Week 1 lab work with a separate Wireshark exercise to document capture preparation, traffic collection, filtering, and packet analysis as I complete each stage.

## 1. Launching Wireshark and reviewing capture interfaces
I launched Wireshark on my Windows host and reviewed the available capture interfaces on the welcome screen.

![Wireshark welcome screen showing available interfaces and Wi-Fi activity before capture](screenshots/01-wireshark-launch.png)

### Observations
The interface list displayed the following adapters:

| Interface | Observation |
| --- | --- |
| WiFi | Highlighted, with an activity sparkline visible |
| Ethernet 5 | Listed as an available capture interface |
| Ethernet 4 | Listed as an available capture interface |
| Adapter for loopback traffic capture | Listed for capturing local loopback traffic |
| Bluetooth Network Connection | Listed as an available capture interface |

The Wi-Fi activity sparkline provided an indication of traffic on that interface. I used this screen to review my capture options before starting a session.

### Capture state
At this stage:
- Wireshark displayed **Ready to load or capture** and **No Packets**.
- No capture file was open and no live capture was underway.
- The capture-filter field was empty.
- The display-filter field was also empty.

The interface names alone do not establish which Ethernet adapter belongs to a particular virtual network. That mapping has not yet been verified in this exercise.

### Technical significance
Capture-interface selection determines where traffic is observed. For this exercise, I first reviewed the available adapters and their activity indicators before collecting evidence. A capture on the Windows host should be interpreted in the context of that host interface; it should not automatically be treated as a direct capture inside the Kali VM.

## 2. Starting a Wi-Fi capture and reviewing initial traffic
I started a packet capture on the **WiFi** interface. The window title changed to **Capturing from WiFi**, and the active capture indicator was visible.

![Wireshark Wi-Fi capture with endpoint identifiers and address-bearing summaries redacted](screenshots/02-wifi-capture-redacted.png)

### Capture status
At the time of the screenshot, the status bar reported **309 packets captured** and **309 displayed (100.0%)**. The display-filter field was empty. The visible packet list showed packets **1–9**, covering approximately **0.375 seconds** from the start of the capture; this is the visible excerpt, not the duration of the complete capture.

### Protocol observations
I reviewed the visible protocol sequence without publishing endpoint addresses:

| Packets | Protocol | Visible behaviour | Analytical significance |
| --- | --- | --- | --- |
| 1–4 | ARP | Two request/reply pairs; requests used a broadcast destination | Local IPv4-to-MAC address resolution |
| 5–6 | DNS | An A-record query and response with matching transaction ID `0x3001` for an internal hostname | A hostname was resolved to an IPv4 address |
| 7–9 | TCP | `SYN`, `SYN, ACK`, then `ACK` between client port `50100` and server port `80` | A TCP three-way handshake is visible |

The ARP frames shown were **42 bytes**, the DNS query and response **82** and **98 bytes**, and the TCP handshake packets **58**, **58**, and **54 bytes**, respectively, as reported in the packet-list Length column.

### TCP handshake interpretation
The visible summaries show:
1. The client sent a **SYN** from port `50100` to port `80`, with relative sequence number `0`.
2. The server replied with **SYN, ACK**, acknowledging relative sequence number `1`.
3. The client completed the handshake with **ACK**, showing relative sequence and acknowledgement numbers of `1`.

The DNS response and subsequent TCP connection involve the same resolved server address in the original screenshot, which is consistent with the client resolving a hostname before opening the connection. This sequence does not by itself establish which application or user action generated the traffic.

### Evidence limits
- Port `80` suggests an HTTP service, but the visible excerpt contains no HTTP request or response. I have not claimed that a page was retrieved or that credentials or other application data were transmitted.
- The screenshot supports an initial protocol review; a saved capture file and expanded packet details have not yet been supplied for deeper validation.
- The displayed ARP, DNS, and TCP activity alone does not demonstrate malicious behaviour.

## Current outcome
I launched Wireshark, started a Wi-Fi capture, and reviewed an excerpt containing ARP resolution, a DNS exchange, and a TCP three-way handshake. Display-filter application and deeper packet inspection remain to be documented.

## Evidence handling
The initial launch screenshot contains no visible IP addresses or packet payloads. For the capture screenshot, Source and Destination values and the address-bearing ARP/DNS Info summaries are covered. These masks also conceal visible MAC identifiers and the internal DNS name. Endpoint values are omitted from this write-up; protocol names, timing, lengths, ports, and TCP flags remain available for analysis. Only the redacted capture image is published here.

## Skills demonstrated so far
Wireshark capture preparation, Wi-Fi traffic collection, ARP and DNS interpretation, TCP handshake analysis, evidence redaction, and technical reporting.
