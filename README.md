# Homelab Automation with Proxmox and NixOS

## Overview
This repository contains a comprehensive setup for automating a homelab environment using Proxmox as the hypervisor, NixOS for host configuration, and OpenTofu/Ansible for resource provisioning and post-provisioning tasks. It also integrates Kubernetes for container orchestration. The goal is to create a highly modular, declarative, and reproducible infrastructure.

---

## Features
- **Proxmox VE**: Open-source hypervisor for managing virtual machines and containers.
- **NixOS**: Declarative operating system to configure the Proxmox host.
- **OpenTofu**: Infrastructure-as-Code (IaC) tool for provisioning VMs and other resources.
- **Ansible**: Procedural configuration management for post-provisioning tasks.
- **Kubernetes**: Orchestration of containerized workloads.
- **Monorepo Structure**: Centralized repository for managing all configurations, scripts, and documentation.

---

## Repository Structure

```
.
├── LICENSE                 # License file
├── README.md               # Project documentation
├── ansible                 # Ansible playbooks and roles for post-provisioning
├── docs
│   ├── adrs               # Architecture Decision Records
│   ├── concepts           # Conceptual explanations
│   ├── diagrams           # Visual diagrams of the infrastructure
│   ├── how-tos            # Step-by-step guides
│   ├── reference          # Reference material
│   └── tutorials          # Tutorials for specific workflows
├── dotfiles                # Config files for shell and editor environments
├── k8s                     # Kubernetes manifests and configurations
├── proxmox
│   ├── host-config        # Proxmox host configuration (NixOS)
│   ├── resource-provisioning # Terraform/OpenTofu configurations for VMs
│   └── scripts            # Utility scripts for managing Proxmox
└── scripts                 # General scripts for automation
```

---

## Architecture Decisions
Key decisions for this project are documented as [Architecture Decision Records (ADRs)](docs/adrs). Here are some highlights:
1. **Use Proxmox as the Hypervisor**: Chosen for its open-source nature, support for KVM and LXC, and rich feature set.
2. **Use NixOS to Configure the Host**: Ensures declarative and reproducible configurations with atomic updates.
3. **Use OpenTofu for Provisioning**: Declarative resource management via the Proxmox API.
4. **Use Ansible for Post-Provisioning**: Automates procedural configurations not handled by NixOS or Terraform/OpenTofu.
5. **Use Kubernetes for Container Orchestration**: Manages scalable container workloads.

---

## Getting Started

### Prerequisites
- **Hardware**: Compatible machine for Proxmox installation.
- **Software**:
  - Proxmox VE 8.3 or higher ([Installation Guide](docs/how-tos/0001-proxmox-installation.md))
  - Terraform/OpenTofu
  - Ansible
  - Kubernetes tools (kubectl, Helm)

---

### Installation Steps
1. **Install Proxmox**:
   - Follow the [Proxmox Installation Guide](docs/how-tos/0001-proxmox-installation.md).

2. **Set Up Networking**:
   - Configure Proxmox networking based on the [Networking Guide](docs/how-tos/0002-proxmox-networking.md).

3. **Install NixOS on the Proxmox Host**:
   - Use the [`proxmox-nixos`](https://github.com/SaumonNet/proxmox-nixos) tool to configure Proxmox on NixOS.
   - Follow the [NixOS Installation Guide](docs/how-tos/0003-installing-nixos-on-proxmox.md).

4. **Provision Resources with OpenTofu**:
   - Define and apply VM configurations as per the [VM Config Guide](docs/how-tos/0005-vm-config-with-tofu.md).

5. **Post-Provisioning with Ansible**:
   - Apply Ansible playbooks for application setup and system customization.

6. **Deploy Kubernetes**:
   - Deploy Kubernetes clusters on provisioned VMs using `kubeadm`, `k3s`, or similar tools.

---

## Documentation
Explore the detailed documentation in the `docs` directory:
- **How-To Guides**: Step-by-step instructions for installation and configuration.
- **Reference Material**: Detailed specifications and technical notes.
- **Tutorials**: Hands-on exercises to master specific tools and workflows.
