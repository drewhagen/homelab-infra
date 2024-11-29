
# Proxmox Networking Guide

## Overview
This guide explains how to configure networking for Proxmox VE, including setting up a bridge network (`vmbr0`) for virtual machines and containers.

---

## Default Network Configuration
Proxmox VE uses a bridged networking model by default, creating a bridge (`vmbr0`) that connects the physical network interface (`eno1`) to virtual machines and containers. This setup allows VMs to appear as separate devices on the same network as the host. See the [Proxmox VE Network Configuration Wiki](https://pve.proxmox.com/wiki/Network_Configuration) for more details.

---

## Example: Static IP Configuration


### Edit `/etc/network/interfaces`
1. Open the file for editing:
   - Use `nano /etc/network/interfaces` to edit the network configuration file.
   
2. Example configuration:
   ```bash
   auto vmbr0
   iface vmbr0 inet static
       address 192.168.1.100
       netmask 255.255.255.0
       gateway 192.168.1.1
       bridge_ports eno1
       bridge_stp off
       bridge_fd 0
   ```
   - `auto vmbr0`: Automatically bring up the bridge interface at boot.
   - `iface vmbr0 inet static`: Define `vmbr0` with a static IPv4 configuration.
   - `address`: The static IP address assigned to the Proxmox host.
   - `netmask`: The subnet mask for the network.
   - `gateway`: The default gateway for outbound traffic.
   - `bridge_ports eno1`: Associate the physical interface `eno1` with the bridge.
   - `bridge_stp off`: Disable Spanning Tree Protocol.
   - `bridge_fd 0`: Set bridge forwarding delay to 0 seconds.

3. Restart networking:
   - Run `systemctl restart networking` to apply the changes. **Note**: Restarting networking services can disrupt active connections, including access to the Proxmox web interface. Proceed with caution, especially if accessing remotely.

---

## Additional Resources
- Learn more about Proxmox VE networking in the [Proxmox VE Administration Guide](https://pve.proxmox.com/pve-docs/pve-admin-guide.html).
- For advanced setups like VLANs or bonded interfaces, refer to the [Proxmox VE Network Configuration Wiki](https://pve.proxmox.com/wiki/Network_Configuration).
- For troubleshooting, review the [Proxmox Community Forum](https://forum.proxmox.com/).

---

## Next Steps
- Verify connectivity by pinging external systems.
- Proceed with installing NixOS as detailed in the [Installing NixOS on Proxmox Guide](docs/how-tos/0003_installing-nixos-on-proxmox.md).
