# PiGuard 🛡️
### Raspberry Pi-Based DNS Filtering & Network Monitoring

PiGuard is a compact, low-power DNS filtering system built using a Raspberry Pi Zero W and Pi-hole. The project explores Linux, networking, DNS security, and embedded systems through practical implementation and testing.

The goal is to develop a standalone device capable of filtering unwanted domains and displaying live network statistics.

## Project Overview

| Category | Description |
|---|---|
| Main Controller | Raspberry Pi Zero W |
| Operating System | Raspberry Pi OS Lite (32-bit) |
| DNS Filtering | Pi-hole |
| Remote Access | SSH |
| Programming | Python, Bash, PowerShell |
| Display | 20×4 I²C LCD (in development) |
| Status | DNS filtering operational |

## Hardware Used

| Component | Purpose |
|---|---|
| Raspberry Pi Zero W | Main processing board |
| 16 GB microSD Card | Operating system storage |
| USB Power Bank | Temporary power supply |
| Windows PC | Configuration and testing |
| 20×4 I²C LCD | Local monitoring display |

## System Setup

Raspberry Pi OS Lite was installed using Raspberry Pi Imager. SSH was enabled to operate the device remotely through Windows PowerShell.

| Setting | Configuration |
|---|---|
| Hostname | `pihole` |
| Username | `ashborn` |
| Local IP | `192.168.0.104` |
| Gateway | `192.168.0.1` |
| Connection | Wi-Fi |

Remote access was established using:

```powershell
ssh ashborn@192.168.0.104
```

A DHCP reservation was configured to maintain a consistent local IP address.

## DNS Filtering with Pi-hole

Pi-hole was installed to filter DNS requests from connected client devices. Cloudflare was configured as the upstream DNS provider.

**DNS request flow:**

`Windows PC → PiGuard → Pi-hole → Upstream DNS`

| Configuration | Value |
|---|---|
| DNS Server | `192.168.0.104` |
| Upstream Provider | Cloudflare |
| Web Dashboard | `http://192.168.0.104/admin/` |
| Filtering | Domain-based blocking |

## DNS Testing & Recovery

The Windows PC was configured to use PiGuard as its preferred DNS server and the router as an alternate DNS server.

DNS filtering was verified through PowerShell:

```powershell
nslookup google.com
nslookup doubleclick.net
```

| Test | Result |
|---|---|
| Normal DNS resolution | Successful |
| Advertising domain blocking | Successful |
| Pi-hole query logging | Verified |
| PiGuard shutdown test | DNS timeout observed |
| Direct router DNS query | Successful |
| PiGuard restart | Filtering recovered |

The shutdown experiment demonstrated how DNS availability affects connectivity and how alternate DNS servers may bypass filtering.

[View Detailed DNS Deployment & Recovery Tests](docs/04-single-device-deployment.md)

## Development Progress

| Feature | Status |
|---|---|
| Raspberry Pi configuration | Completed |
| SSH and network setup | Completed |
| Pi-hole installation | Completed |
| DNS filtering and testing | Completed |
| Python monitoring | In development |
| I²C LCD dashboard | In development |
| 3D-printed enclosure | Planned |
| Portable deployment | Planned |

## Technologies & Skills

**Linux • Raspberry Pi • DNS • DHCP • SSH • Pi-hole • Python • PowerShell • I²C • CAD • 3D Printing**

PiGuard is an ongoing project combining networking, programming, and electronics into a standalone embedded system.
