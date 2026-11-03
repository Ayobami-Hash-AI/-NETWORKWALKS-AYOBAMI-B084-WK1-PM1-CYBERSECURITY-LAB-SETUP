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

## Current outcome
I successfully opened Wireshark and identified the Wi-Fi interface as showing activity. Packet collection, protocol identification, filter application, and traffic findings will be documented as I complete those steps.

## Evidence handling
This initial screenshot contains no visible IP addresses or packet payloads. Subsequent screenshots will be reviewed for IP addresses and other sensitive details before publication.

## Skills demonstrated so far
Wireshark interface navigation, capture-interface review, and accurate documentation of capture state.
