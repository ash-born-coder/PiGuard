# System Preparation and Verification

## Overview

After successfully installing Raspberry Pi OS Lite and establishing an SSH connection in Milestone 1, the next step was to prepare my Raspberry Pi Zero W for running Pi-hole.

Before installing any additional software, I wanted to make sure the operating system was up to date, the hardware had enough available resources, and the network connection was working correctly.

This milestone also gave me an opportunity to become more familiar with Linux commands and understand how to manage and troubleshoot a Raspberry Pi remotely.

## 1. Updating Raspberry Pi OS

I started by updating the package lists:

```bash
sudo apt update
```

The Raspberry Pi successfully connected to the software repositories and downloaded the latest package information. The terminal reported that 23 installed packages had updates available.

I then upgraded the system using:

```bash
sudo apt full-upgrade -y
```

After completing the upgrade, I restarted the Raspberry Pi:

```bash
sudo reboot
```

This was my first experience updating and restarting a Linux system entirely through SSH.

### A small problem after rebooting

When the Raspberry Pi restarted, my SSH connection was disconnected, which was expected.

However, when I tried reconnecting using:

```powershell
ssh ashborn@pihole.local
```

Windows initially couldn't resolve the hostname.

Since I had previously identified the Raspberry Pi's local IP address, I could also try connecting directly using:

```powershell
ssh ashborn@192.168.0.104
```

The Raspberry Pi became accessible again, and I was able to continue working.

This helped me understand the difference between connecting to a device through its hostname and connecting directly through its IP address.

## 2. Checking Storage and Memory

With the Raspberry Pi running again, I wanted to see how much of its limited hardware resources were being used.

### Storage

I checked the available storage using:

```bash
df -h /
```

The results were:

| Total Storage | Used | Available | Usage |
|---|---|---|---|
| 14 GB | 2.1 GB | 12 GB | 16% |

The operating system was using only a small portion of the available storage, leaving plenty of room for Pi-hole and the additional software I plan to develop.

### RAM and Swap

Next, I checked memory usage:

```bash
free -h
```

| Memory | Total | Used | Available |
|---|---|---|---|
| RAM | 426 MiB | 115 MiB | 311 MiB |
| Swap | 425 MiB | 0 B | 425 MiB |

Since the Raspberry Pi Zero W has only 512 MB of physical RAM, I wanted to make sure it wasn't already using too much memory before adding more services.

At the time of testing, the system had approximately 311 MiB of available RAM and wasn't using swap.

These results gave me a useful starting point for comparing resource usage after installing Pi-hole.

## 3. Testing the Internet Connection

Before setting up a DNS-based ad blocker, I needed to confirm that the Raspberry Pi could communicate with external servers.

I tested the connection using:

```bash
ping -c 4 1.1.1.1
```

The test returned:

- 4 packets transmitted
- 4 packets received
- 0% packet loss
- Average response time: approximately 22.4 ms

All four packets were received successfully, confirming that the Raspberry Pi had a working internet connection.

## 4. Verifying DNS Resolution

Since Pi-hole works by filtering DNS requests, understanding DNS is an important part of this project.

I tested the Raspberry Pi's existing DNS resolution using:

```bash
getent hosts github.com
```

The command returned an IP address for `github.com`, confirming that domain-name resolution was working.

This was an important check because Pi-hole will eventually become the DNS server used by devices on my local network.

At this stage, Pi-hole had not been installed, so the Raspberry Pi was still using its existing DNS configuration.

## 5. Understanding the Network Configuration

I then inspected the Raspberry Pi's network routes:

```bash
ip -4 route
```

This helped me identify the default gateway, local network, and active network interface.

| Parameter | Value |
|---|---|
| Hostname | pihole |
| Network Interface | wlan0 (Wi-Fi) |
| Local IP Address | 192.168.0.104 |
| Default Gateway | 192.168.0.1 |
| Network | 192.168.0.0/24 |
| IP Assignment | DHCP |

I also checked the Wi-Fi interface's MAC address using:

```bash
cat /sys/class/net/wlan0/address
```

The reason for checking these details was to prepare for the next stage of the project.

Pi-hole needs a reliable IP address because other devices will use it to resolve domain names. My next task is to configure a DHCP reservation so that the router continues assigning the same IP address to the Raspberry Pi.

For now, the network configuration has only been inspected, not modified.

## 6. What I Learned

Although this milestone didn't involve writing much code, it helped me become more comfortable working with Linux.

Some of the main things I learned were:

- How to update and upgrade a Debian-based operating system.
- How to restart a remote device and reconnect through SSH.
- The difference between a hostname and an IP address.
- How to inspect storage, RAM, and swap usage.
- How to test internet connectivity and DNS resolution.
- How to identify a network gateway, interface, and MAC address.
- Why a stable local IP address matters when running a network service.

I also started to understand the importance of testing a system before installing additional software, especially when working with hardware that has limited resources.

## 7. Milestone Outcome

By the end of this milestone, I had successfully:

- Updated the Raspberry Pi's package information and initiated the system upgrade.
- Rebooted and reconnected to the Raspberry Pi through SSH.
- Verified available storage and memory.
- Confirmed that internet connectivity was working.
- Verified DNS resolution.
- Identified the network settings needed for the next stage.

The Raspberry Pi Zero W is now ready for the next phase of PiGuard.

**Next milestone: Installing Pi-hole, configuring a stable network address, and testing DNS-based ad blocking.**

---

*Project: PiGuard — Raspberry Pi Zero W Network Ad Blocker*

*Milestone 02: Completed — November 2026*
