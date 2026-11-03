# PiGuard — Raspberry Pi Network Ad Blocker & Monitoring System

## About the Project

PiGuard is a personal project I'm working on using a Raspberry Pi Zero W. The main idea is to build a small, low-power device that can block unwanted ads and tracking domains across my home network using Pi-hole.

However, I don't want this project to be just about installing an ad blocker. I want to take it a step further by building a complete device from scratch, including the software, hardware integration, and a custom 3D-printed enclosure.

As an Information Engineering student, I'm interested in exploring how different technologies work together. Through this project, I want to improve my understanding of Linux, computer networking, Python programming, and hardware interfacing, while also developing my CAD and 3D-printing skills.

I'll be documenting the entire development process here, including the challenges I run into, the solutions I find, and the improvements I make along the way.

## What I'm Planning to Build

The project will be developed in several stages:

1. **Network-wide Ad Blocking:** Set up Pi-hole on the Raspberry Pi Zero W to filter DNS requests and block known advertising and tracking domains.

2. **Network Monitoring:** Develop a Python application that collects information such as the number of DNS queries, blocked requests, and system performance.

3. **LCD Display:** Connect a 20×4 I²C LCD to display useful information directly on the device without needing to open a web dashboard.

4. **Custom Housing:** Design and 3D-print a compact enclosure to keep the Raspberry Pi, LCD, and wiring neatly organized.

5. **Testing and Improvements:** Test the system's reliability, monitor its performance, and make improvements based on the results.

## Hardware

### Initial Hardware Setup

The Raspberry Pi Zero W used for this project.

![Raspberry Pi Zero W](images/hardware/Pi%20zero%2001.jpeg)

![Initial Hardware Setup](images/hardware/Pi%20zero%2002.jpeg)

| Component | Purpose |
|---|---|
| Raspberry Pi Zero W | Main computer running Pi-hole |
| 16 GB microSD card | Operating system and storage |
| 5 V USB power supply | Powering the Raspberry Pi |
| 20×4 I²C LCD | Displaying network statistics |
| I²C level shifter | Safe interfacing between the LCD and Raspberry Pi, if required |
| Custom 3D-printed enclosure | Housing the complete system |

## Software and Tools

- **Raspberry Pi OS Lite (32-bit)** — Operating system
- **Pi-hole** — DNS-based ad and tracker blocking
- **Python** — Monitoring and LCD programming
- **Linux and SSH** — Remote access and system configuration
- **FreeCAD** — Designing the enclosure
- **Anycubic Slicer Next** — Preparing the design for 3D printing
- **GitHub** — Documenting and tracking project development

## Project Progress

- [x] Choose the Raspberry Pi and required hardware
- [x] Flash Raspberry Pi OS Lite onto the microSD card
- [ ] Connect to the Raspberry Pi through SSH
- [ ] Install and configure Pi-hole
- [ ] Test DNS filtering
- [ ] Develop the Python monitoring application
- [ ] Connect and program the LCD
- [ ] Design the enclosure in CAD
- [ ] 3D-print and assemble the enclosure
- [ ] Test the completed system

## Documentation

I'm using this repository to document the project as I build it, rather than only sharing the finished result.

I'll be including setup instructions, hardware photographs, wiring diagrams, Python code, CAD models, troubleshooting notes, and testing results.

I also plan to document the enclosure design process, including the initial models, prototype prints, any problems with fitting the components, and the changes made to improve the final design.

## Current Status

**In Progress — Raspberry Pi OS Setup**

I've selected the hardware and flashed Raspberry Pi OS Lite onto the microSD card. The next step is to establish an SSH connection and begin configuring Pi-hole.

## Future Improvements

Once the basic system is working, I'd like to explore additional features such as:

- Historical network statistics and graphs
- Automatic startup and recovery after power interruptions
- Improved system monitoring and diagnostics
- Integration with other Raspberry Pi projects

## Final Goal

My goal is to end up with a compact, reliable device that I can actually use every day, while gaining practical experience in software development, networking, electronics, and mechanical design.

This repository will serve as both a record of what I've learned and a portfolio of the work I've completed.
