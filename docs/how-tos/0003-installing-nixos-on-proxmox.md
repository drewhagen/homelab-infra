# Installing NixOS on Proxmox with `proxmox-nixos`

## Overview
This guide explains how to use the [`proxmox-nixos`](https://github.com/SaumonNet/proxmox-nixos) project to set up and manage NixOS on Proxmox VE declaratively. The project enables seamless integration of Proxmox and NixOS, allowing for declarative management of both the hypervisor and virtual machines.

---

## Prerequisites
- An operational Proxmox VE host. Refer to the [Proxmox VE Installation Guide](docs/how-tos/0001_proxmox-installation.md).
- A working NixOS system with Flakes enabled. Refer to the [NixOS Manual](https://nixos.org/manual/nixos/stable/).
- Familiarity with NixOS configuration and Proxmox concepts.

---

## Steps

### 1. Clone the `proxmox-nixos` Repository
1. Open a terminal on your NixOS system or another machine with Nix installed.
2. Clone the repository:
   ```bash
   git clone https://github.com/SaumonNet/proxmox-nixos.git
   cd proxmox-nixos
   ```
3. Review the README for additional details: [proxmox-nixos README](https://github.com/SaumonNet/proxmox-nixos).

---

### 2. Configure Proxmox on NixOS
To run Proxmox VE on NixOS, add the Proxmox service module to your NixOS configuration.

1. Edit your NixOS configuration file, usually located at `/etc/nixos/configuration.nix`, to include the Proxmox module:
   ```nix
   {
     services.proxmox = {
       enable = true;
       webUi.enable = true;
     };

     networking.interfaces.enp0s3 = {
       ipv4.addresses = [{
         address = "192.168.1.100";
         prefixLength = 24;
       }];
       ipv4.gateway = "192.168.1.1";
     };
   }
   ```
2. Rebuild the system to apply changes:
   `nixos-rebuild switch`

---

### 3. Use `nixmoxer` for Bootstrapping
The `nixmoxer` tool simplifies bootstrapping VMs using Proxmox's API.

1. Run `nixmoxer` to create a VM from a configuration file:
   `nix run github:SaumonNet/proxmox-nixos#nixmoxer -- [--flake] vm-config`
2. Replace `vm-config` with the path to your VM configuration file.

For more details, see the [nixmoxer usage documentation](https://github.com/SaumonNet/proxmox-nixos#nixmoxer).

---

### 4. Networking Configuration
1. Ensure your Proxmox host is configured with a bridge (`vmbr0`).
   - Refer to the [Proxmox Networking Guide](docs/how-tos/0002_proxmox-networking.md) for setup instructions.
2. Update your NixOS configuration to match the bridge settings for VM networking.

---

## Why OpenTofu for VM Management?
OpenTofu is a declarative Infrastructure-as-Code (IaC) tool that integrates with Proxmox via its API, making it ideal for managing the lifecycle of virtual machines. By using OpenTofu, you can:
- Define VM configurations in a version-controlled manner.
- Apply, update, or destroy VMs consistently across environments.
- Manage additional infrastructure resources alongside Proxmox VMs.

While VMs can also be declaratively managed using `proxmox-nixos`, OpenTofu offers a more specialized approach for VM lifecycle management. It follows an industry standard IaC that can be used in conjuction with NixOS for a comprehensive infrastructure setup.

For instructions on setting up OpenTofu for Proxmox, see the [OpenTofu Proxmox Guide](docs/how-tos/0005_opentofu-proxmox.md).

---

## Additional Resources
- [proxmox-nixos GitHub Repository](https://github.com/SaumonNet/proxmox-nixos): Includes comprehensive details on setup and usage.
- [NixOS Manual](https://nixos.org/manual/nixos/stable/): Reference for declarative configurations.
- [Proxmox VE Documentation](https://pve.proxmox.com/pve-docs/): Official Proxmox documentation.
- [Proxmox Networking Wiki](https://pve.proxmox.com/wiki/Network_Configuration): Advanced networking setups.
- [NixOS Discourse Announcement](https://discourse.nixos.org/t/announcing-proxmox-nixos/47579): Community discussions and updates.

---

## Next Steps
- Use the declarative NixOS approach to manage Proxmox VMs and services.
- Explore advanced features of `proxmox-nixos`, such as managing multiple nodes or enabling high availability.
- Customize your NixOS configurations further to optimize your Proxmox-NixOS integration.
