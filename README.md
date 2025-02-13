# setup-docs
Personal documentation of my tech stack, homelab, and experiments across my devices.



**Currently, this is just a template I've build to give myself an outline to work on**
**None of the current content is the actual content of mine**


## Table of Contents
- [Introduction](#introduction)
- [Devices & Infrastructure](#devices--infrastructure)
- [Software & Services](#software--services)
- [Configuration & Setup](#configuration--setup)
- [Automation & Scripting](#automation--scripting)
- [Troubleshooting & Notes](#troubleshooting--notes)
- [Future Plans](#future-plans)

## Introduction
This repository serves as my personal knowledge base, documenting my tech stack, home lab setup,
 and various configurations across my **Synology NAS, MacBook Air and PC** 
 and other devices. It includes:

- System setups – Operating systems, configurations and tips and tricks.
- Self-hosted services – Applications running on my NAS and PC.
- Automation & scripting – Custom backups, Scripts and other Automations.
- Networking & infrastructure – Router configurations, VPN setup, and Docker containers.
- Troubleshooting logs – Some of the technical issues I’ve encountered and how I solved them.
- Smart Home Setup - Zigbee network, Home Assistant integrations, and automations.

## Devices & Infrastructure
### Primary Laptop
- MacBook Air 
  - Processor: Apple M1 
  - Memory: 8GB
  - Storage: 256GB

### PC
- Legion T530-28ICB
  - Processor: Intel i7-9700 8 Cores @ 4.700GHz
  - Memory: 16GB Lenovo
  - GPU: NVIDIA GeForce GTX 1660 Ti
  - Storage 1: 256GB SAMSUNG MZVLB256HAHQ-000L7
  - Storage 2: 2TB WD(Green) Seagate Barracuda ST2000DM008
  - Storage 3: 4TB WD(Blue) WDC WD40EZAZ-22SF3B0
### NAS
- Synology DS923+
  - Processor: AMD Ryzen Embedded R1600
  - Memory: 4GB
  - Storage 1: Synology Model HAT5300-4T
  - Storage 2: Synology Model HAT5300-4T (Backup, more in that later)
 
  
### Network
Model names and   aren't 
- Router: (5G)
- Switch1: Cisco POE
- Switch2&3: (WIP)
- Network Video Recorder (NVR): Hikvision


- Work in progress!

- GrandStream IP Phones
- Tailscale VPN

### Smart Home
Home Assistant, Zigbee network, automations

More details inside the [`/infrastructure`](./infrastructure) folder.

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
