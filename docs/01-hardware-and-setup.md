# 01 — Hardware and Initial Setup

## Objective

The first stage of PiGuard focuses on preparing the Raspberry Pi Zero W to run as a small, low-power network filtering server.

Before installing Pi-hole, I need to set up the operating system, configure network connectivity, and establish remote access through SSH.

## Hardware Used

| Component | Description |
|---|---|
| Raspberry Pi Zero W | Main processing board |
| 16 GB microSD card | Operating system storage |
| USB power bank | Temporary power source for initial testing |
| Windows PC | Used for OS installation and remote access |

A 20×4 I²C LCD and custom 3D-printed enclosure are planned for later stages.

## Operating System Installation

I selected Raspberry Pi OS Lite (32-bit) because I don't need a full desktop environment for a dedicated DNS filtering server.

I used Raspberry Pi Imager to write the operating system to the microSD card.

During configuration, I planned the following settings:

- Hostname: `pihole`
- Username: `ashborn`
- SSH: Enabled with password authentication
- Wi-Fi: Configured for the local wireless network

The operating system image was successfully written to the microSD card.

## Initial Challenges

During an earlier setup attempt, I was unable to connect to the Raspberry Pi using its hostname.

To investigate the issue, I used Windows PowerShell commands such as:

```powershell
ipconfig
arp -a
ping 192.168.0.100
Test-NetConnection 192.168.0.100 -Port 22
```

Although some devices responded to ping, SSH was not accessible at the tested addresses. I couldn't confirm that either device was the Raspberry Pi.

Since I wasn't sure whether Wi-Fi and SSH had been configured correctly, I decided to reflash the operating system with the necessary settings enabled.

## Current Progress

- [x] Select Raspberry Pi hardware
- [x] Prepare microSD card
- [x] Write Raspberry Pi OS Lite
- [ ] Boot the Raspberry Pi Zero W
- [ ] Establish SSH connection
- [ ] Verify the operating system

## Next Step

Boot the Raspberry Pi Zero W and establish a successful SSH connection before installing Pi-hole.
