# 2. Use Proxmox as the Hypervisor

## Context
We need a hypervisor to manage virtual machines (VMs) and containers for the homelab. The hypervisor must:
- Be open-source and free or affordable.
- Support KVM for VMs and LXC for lightweight containers.
- Integrate well with other tools for automation and configuration management.

## Decision
We will use **Proxmox VE** as the hypervisor for the homelab.

## Rationale
1. **Features**:
   - Proxmox supports both KVM for full virtualization and LXC for containers.
   - It includes built-in features like snapshots, high availability, and clustering.
2. **Ease of Use**:
   - Proxmox provides an intuitive web interface for managing resources.
   - It has an active community and extensive documentation.
3. **Integration**:
   - Proxmox integrates with Terraform/OpenTofu for declarative resource management.
   - It supports advanced networking and storage options like ZFS.
4. **Cost**:
   - Proxmox is free and open-source, with an optional paid support model.

## Consequences
- Proxmox will be the foundation of our homelab.
- Future decisions on networking, storage, and resource provisioning must align with Proxmox’s capabilities and limitations.
