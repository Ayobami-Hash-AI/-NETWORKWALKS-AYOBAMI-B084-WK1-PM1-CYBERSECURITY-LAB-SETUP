# Networkwalks Cybersecurity Lab Setup
**Author:** Ayobami Odulaja | **Cohort:** B084 | **Module:** WK1 PM1

## Objective
I prepared a Windows host and added a Kali Linux virtual machine to Oracle VirtualBox to establish a foundation for my cybersecurity lab exercises.

## 1. Host preparation
I downloaded and installed 7-Zip and Oracle VirtualBox on my host machine. 7-Zip provides archive extraction, while VirtualBox provides the virtualization platform for running the lab VM.

The installer files shown below are `7z2605-x64` and `VirtualBox-7.2.22-175245-Win`. Their presence documents the downloaded installers; the VirtualBox screenshot in the next section also confirms that VirtualBox was running.

![Downloaded 7-Zip and VirtualBox installers](screenshots/host-installers.png)

## 2. Kali Linux VM setup
After preparing the host, I downloaded the Kali Linux VirtualBox VM package and added the VM to VirtualBox. I used the prebuilt VM rather than documenting an ISO-based operating system installation.

The registered VM is named `kali-linux-2026.1-virtualbox-amd64`. In the screenshot below, VirtualBox shows it in the **Powered Off** state.

## 3. Baseline snapshot
I created a baseline snapshot named **Netwalk-Kali-Lab-Setup** to preserve the initial lab state before further changes.

![Kali Linux VM in VirtualBox with the Netwalk-Kali-Lab-Setup snapshot](screenshots/kali-baseline-snapshot.png)

A snapshot provides a rollback point and depends on the VM's underlying virtual disks. It is not an independent backup. This repository contains documentation and screenshot evidence; VM disk and snapshot files are stored separately.

## 4. NAT network configuration
I configured a NAT network in VirtualBox's Network Manager to provide a shared network for lab VMs.

| Setting | Configuration |
| --- | --- |
| Network name | `NatNetwork` |
| IPv4 subnet | `10.0.0.0/24` |
| Subnet mask | `255.255.255.0` |
| DHCP | Enabled |
| IPv6 | Disabled |

I enabled DHCP to support automatic IPv4 address allocation for VMs attached to this network. The shared NAT network is intended to support communication between attached lab VMs and outbound access through the host.

![VirtualBox NAT network settings showing NatNetwork, 10.0.0.0/24, DHCP enabled and IPv6 disabled](screenshots/virtualbox-nat-network.png)

This screenshot records the network configuration. Guest IP assignment, communication between VMs, and internet access still require validation from inside the guest.

## Outcome and evidence
- I installed the host utilities and registered the Kali Linux VM in VirtualBox.
- I established a named baseline snapshot for subsequent lab work.
- I configured the `NatNetwork` IPv4 subnet with DHCP enabled and IPv6 disabled.
- The screenshots document the downloaded installers and the powered-off VM with its snapshot name.
- Guest boot, login, and network connectivity have not yet been demonstrated in this entry.

## Skills demonstrated
Host preparation, virtualization setup, VM registration, snapshot management, NAT networking, DHCP configuration, and evidence-based technical documentation.
