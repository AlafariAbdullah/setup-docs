# setup-docs

**Personal documentation of my tech stack, homelab, and experiments across my devices.**

---

⚠ **Currently, this is just a template I've built to give myself an outline to work on.**

⚠ **None of the current content is the actual content of mine.**

---

## 📖 Table of Contents

- [Introduction](#introduction)
- [Devices & Infrastructure](#devices--infrastructure)
- [Software & Services](#software--services)
- [Configuration & Setup](#configuration--setup)
- [Automation & Scripting](#automation--scripting)
- [Troubleshooting & Notes](#troubleshooting--notes)
- [Future Plans](#future-plans)

---

## 📝 Introduction

This repository serves as my **personal knowledge base**, documenting my **tech stack, home lab setup,** and various configurations across my **Synology NAS, MacBook Air, PC,** and other devices. It includes:

- **System setups** – Operating systems, configurations, tips, and tricks.
- **Self-hosted services** – Applications running on my NAS and PC.
- **Automation & scripting** – Custom backups, scripts, and other automations.
- **Networking & infrastructure** – Router configurations, VPN setup, and Docker containers.
- **Troubleshooting logs** – Some of the technical issues I’ve encountered and how I solved them.
- **Smart Home Setup** – Zigbee network, Home Assistant integrations, and automations.

---

## 🖥️ Devices & Infrastructure

### 🌐 **Network**  
_Identifiable specifications and model numbers aren't here for obvious security reasons 🙂_

- **Router**: ZTE (5G)
- **Switch 1**: Cisco POE / 2x Ports
- **Switch 2 & 3**: _(Currently Down)_
- **Network Video Recorder (NVR)**: Hikvision PoE
- **GrandStream Private Branch Exchange (PBX)** - Private IP Phone Network
- **GrandStream IP Phones & Intercoms**
- [**Tailscale VPN**](https://tailscale.com/)

### 📦 **Network Attached Storage (NAS)** - Synology DS923+

- **Processor**: AMD Ryzen Embedded R1600
- **Memory**: 4GB
- **Storage 1**: Synology Model HAT5300-4T
- **Storage 2**: Synology Model HAT5300-4T _(Backup, more on that in the future)_

### 💻 **Primary Laptop** - MacBook Air

- **Processor**: Apple M1
- **Memory**: 8GB
- **Storage**: 256GB

### 🖥️ **PC** - Legion T530-28ICB

- **Processor**: Intel i7-9700 (8 Cores @ 4.700GHz)
- **Memory**: 16GB Lenovo
- **GPU**: NVIDIA GeForce GTX 1660 Ti
- **Storage 1**: 256GB SAMSUNG MZVLB256HAHQ-000L7
- **Storage 2**: 2TB WD (Green) Seagate Barracuda ST2000DM008
- **Storage 3**: 4TB WD (Blue) WDC WD40EZAZ-22SF3B0

### 🏡 **Smart Home**
Managing Zigbee devices, automations, and integrating controls for [SmartTVs](https://www.home-assistant.io/integrations/#media-player) and Media Servers([dlna](https://www.dlna.org/), [PLEX](https://www.plex.tv/), [Jellyfin](https://github.com/jellyfin/jellyfin), and more) for seamless smart dashboard control. (Work in Progress)
- **Backend**: [Home Assistant](https://github.com/home-assistant)

- **Protocols**: Zigbee ([ZHA](https://www.home-assistant.io/integrations/zha/)), [Android Debugging Bridge (ADB)](https://developer.android.com/tools/adb), [Secure Shell (SSH)](https://datatracker.ietf.org/doc/html/rfc4251), [WireGuard](https://www.wireguard.com/) via [Tailscale](https://tailscale.com/), [RTSP](https://datatracker.ietf.org/doc/html/rfc2326).
etc.
- **Devices**:
  - **Zigbee Coordinator**: [SMLIGHT SLZB-06 PoE](https://smlight.tech/product/slzb-06/)
  - **Lighting**: Moes light siwtches (a mix of 1, 2 and 3 gang switches)
  - **Sensors**: Moes Motion, temperature, humidity, and door open/close sensor
  - **Cameras & Security**: IP cameras, NVR setup, and a smart door lock
  - **Blinds**: Moes Zigbee Blind Switch
  - **Entertainment & Media**: AppleTV, TCL Android TV, [Plex Media Server](https://www.plex.tv/), [Jellyfin](https://github.com/jellyfin/jellyfin) and [DLNA]((https://www.dlna.org/)) (Details later)
- **Automation & Scenes**: Custom automations for lighting, blinds, media, and routines
- **Voice Control**: Alexa (Work in progress)
- **Remote Access & Security**: [Tailscale VPN](https://tailscale.com/), Multi-factor authentication (via Email and OTP Apps)

## Software & Services
### Operating Systems
macOS, Linux (Ubuntu, Debian, Arch?), Windows

### Essential Tools
Docker, VS Code, Tailscale, SSH, etc.

### Self-Hosted Services
#### Docker Containers
[List services]

#### Reverse Proxy & Network
[NGINX, Traefik?]

#### Home Automation
Home Assistant, MQTT, Zigbee2MQTT

#### Storage & Backup
Synology, rsync, cloud backups

More details inside the [`/software`](./software) and [`/services`](./services) folders.

## Configuration & Setup
### Dotfiles & Scripts
Zsh, Bash, Git, VS Code, aliases, SSH configs

### Home Assistant Automations
YAML configs, Zigbee, MQTT

### Docker & Self-Hosting Setup
Compose files, deployment strategies

### Networking Configurations
Firewall rules, VPNs, VLAN setup

## Automation & Scripting
### Shell Scripts & Cron Jobs
Automation scripts for various tasks

### Home Assistant YAML & Node-RED Automations
Smart home automations and integrations

### Python Tools & CLI Utilities
Custom scripts and utilities for system management

## Troubleshooting & Notes
### Common Issues & Fixes
Documented issues and their resolutions

### Networking & Firewall Debugging
Notes on firewall and VPN troubleshooting

### Docker & Service Logs
Logs and debugging tips for containerized services

## Future Plans
### Improve My Homelab Networking
Optimizing VLANs, firewall rules, and VPNs

### Expand Smart Home Automations
More integrations and intelligent automations

### Experiment with New Self-Hosted Services
Testing and deploying new tools

### Document More Detailed Configurations
Improve structure and add more examples

---
