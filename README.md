# Home Server
A personal home server built to explore self-hosting, infrastructure, networking, and automation.

## Overview
This documentation provides an overview of my home server project: why I built it, what problems it solves, and the goals I aimed to achieve. The server is built using my old PC (PowerSpec G315) and a Raspberry Pi 5. The PC provides the main hardware resources, while the Raspberry Pi handles networking duties to complete the setup.

I chose to start this project to gain hands-on experience with virtualization, deepen my understanding of Linux systems, and leverage an x86 processor for applications where my MacBook Air M2 has limitations. This server solves several daily problems, including running x86-specific programming environments and experimenting with different operating systems like Kali Linux, Ubuntu/Tuffix, Windows, and TrueNAS.

## Motivation and Goals
The main reasons I started this project were to develop practical skills in system administration and virtualization and to explore Linux in a multi-OS environment. I was inspired by online tutorials, courses, and my curiosity to build a flexible, production-like lab at home that allows me to experiment safely and learn continuously.

## Technology Stack
- **Hardware** –
  - ASUS Prime Z370-P
  - Intel i5-8600k
  - GTX 1070
  - 2x8GB DDR4 3000MHz RAM
  - 240GB SATA SSD
  - WiFi Card

- **Operating System** –
  - Proxmox (host OS)
  - Kali Linux (VM)
  - Ubuntu/Tuffix (VM)
  - Linux From Scratch (LFS) (VM)
  
- **Virtualization / Containers** –
  - Virtual Machines (VMs)
  - LXC (Linux Containers)
  - Docker
 
- **Networking** –
  - Raspberry Pi 5 (router and network manager)
  - Tailscale VPN Mesh
  - Pi-Hole (DNS filtering) 
  
- **Storage & Backups** –
  - 240GB SATA SSD (OS and VM storage)
  - Backup strategy planned (see below)

- **Monitoring & Management** –

## Architecture Overview
**Hardware Overview**

The Intel i5 CPU with 6 cores and 12 threads is allocated among my VMs to maximize performance. The GTX 1070 GPU is passed through to a VM via PCI-e passthrough for GPU-intensive tasks. Similarly, the WiFi card is passed through to the Kali Linux VM for wireless security testing. The 16GB RAM is shared across the VMs, and the 240GB SSD stores the OS and VM data.

**Virtualization & Containerization Approach**

Proxmox is the main hypervisor managing all VMs and containers. The setup uses a combination of full VMs and lightweight LXC containers to balance flexibility and efficiency.

**Network Layout**

Due to lack of direct Ethernet access in my room, I configured my Raspberry Pi to act as a router for the PC/server. Connected by Ethernet, the PC treats the Pi as its internet source, enabling proper Proxmox operation and networking. The Pi also manages IP addresses, DNS requests (via Pi-Hole), and internet traffic for the server and all VMs.

**Storage Strategy**

Currently, the server relies on a single 240GB SSD for the OS and VMs. In the future, I plan to add a 1TB HDD for expanded storage and eventually build a NAS and media server.

**Diagrams**

  - Insert architecture diagram here
  - Insert network diagram here




## Services and Applications


## Security Considerations
**Network segmentation:** Separate VLANs or virtual networks isolate critical systems and VMs.

**Authentication:** Strong passwords and SSH key authentication for remote access.

**Secrets management:** Sensitive credentials stored securely and rotated periodically.

**Updates and patching:** Regular OS and application updates to address vulnerabilities.

**Backup and recovery:** Plan to implement scheduled backups once additional storage is available, using Proxmox’s built-in backup features.

## Setup and Deployment
- Initial provisioning involved installing Proxmox directly on the PC.

- The Raspberry Pi was configured as a router with Pi-Hole and Tailscale for VPN access.

- VMs and containers are created and managed via Proxmox’s web interface.

- Automation is limited currently but could be expanded using Ansible or similar tools in the future.

## What I Learned
- Gained hands-on experience with Proxmox virtualization and containerization.

- Deepened understanding of Linux networking, firewalling, and routing via Raspberry Pi.

- Learned PCI-e passthrough configuration for GPU and WiFi cards.

- Understood the importance of proper storage planning and backup strategies.

- Improved troubleshooting and debugging skills through network and VM setup issues.

## Challenges Faced
- Overcoming lack of direct Ethernet access with Raspberry Pi routing was a key challenge.

- Configuring PCI-e passthrough required extensive research and trial-and-error.

- Managing resource allocation to avoid performance bottlenecks was an ongoing learning process.

- Encountered networking conflicts that required careful IP and subnet management.

## Future Improvements and Roadmap
**Short-term:** Add a dedicated HDD to expand storage capacity. Implement scheduled backups for data safety.

**Medium-term:** Build a NAS and media server for centralized file storage and streaming.

**Long-term:** Automate deployment and updates with configuration management tools (Ansible, Terraform). Explore Kubernetes or other orchestration for container management.

Enhance monitoring and alerting for system health and security events.
