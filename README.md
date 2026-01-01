# NetLab: Router Configuration & Routing

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Network](https://img.shields.io/badge/Focus-Networking-blue.svg)](#)

A comprehensive documentation and lab repository focused on advanced computer network configurations, specifically routing protocols, interface management, and network troubleshooting.

## 🚀 Project Overview

This repository contains practical implementations and configurations for complex network topologies. It covers the following key areas:

- **Static Routing:** Configuration and verification of routes across multiple routers (R1-R4).
- **Network Troubleshooting:** Usage of diagnostic tools like `ping`, `traceroute`, and `ip route`.
- **Interface Management:** Detailed steps for managing virtual interfaces and handling network failovers.
- **Verification:** Practical execution steps for validating network connectivity in multi-hop environments.

## 📁 Repository Structure

- `REDES DE ORDENADORES.docx`: Main documentation containing lab procedures, commands, and expected results.
- `GEMINI.md`: Contextual documentation for AI-assisted development and analysis.

## 🛠️ Key Commands Used

### Host Diagnostics
```bash
# Check routing tables
ip route show

# Check interface addresses
ip address show

# Verify connectivity
ping -c3 <TARGET_IP>
```

### Router Management (Cisco-style)
```bash
# View running configuration
show running-config

# View routing table
show ip route
```

## 📖 How to Use

1. **Review the Documentation:** Start with `REDES DE ORDENADORES.docx` to understand the topology and objectives.
2. **Follow the Hitos:** The project is structured in milestones (Hitos) for incremental learning.
3. **Simulate:** Use these configurations in network simulators like GNS3 or Cisco Packet Tracer to replicate the lab environment.

## ✍️ Authors

- **Iván Sebastián Loor Weir**
- **Álvaro González Fúnez**

---
*Developed for Computer Networking practices.*
