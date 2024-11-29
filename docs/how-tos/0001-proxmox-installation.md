
# Proxmox VE Installation Guide

## Overview
This guide explains how to install Proxmox VE 8.3 on a server from the official ISO. Proxmox is a hypervisor for managing virtual machines and containers.

---

## Prerequisites
- A compatible server or machine.  
- [Proxmox VE 8.3 ISO](https://www.proxmox.com/en/downloads/proxmox-virtual-environment/iso/proxmox-ve-8-3-iso-installer).  
- A USB drive (minimum 2GB) for bootable media.

---

## Steps

### 1. Create Bootable Media  
1. Download the Proxmox VE 8.3 ISO from the [official Proxmox downloads page](https://www.proxmox.com/en/downloads).  
2. Create a bootable USB using tools like **Rufus** (Windows) or `dd` (Linux).
   ```bash
   sudo dd if=proxmox-ve_8.3.iso of=/dev/sdX bs=4M status=progress
   ```  
   - **Using `dd` on Linux**:  
     - Replace `/dev/sdX` with your USB drive's device identifier.  
   - **Using Rufus on Windows**:  
     - Download and open [Rufus](https://rufus.ie/).  
     - Select the Proxmox VE 8.3 ISO and your USB drive.  
     - Click "Start" to create the bootable USB.  

For detailed instructions, refer to the [Proxmox VE Installation Guide](https://pve.proxmox.com/pve-docs/chapter-pve-installation.html).


---

### 2. Install Proxmox VE  
1. Insert the bootable USB into your server and boot from it.  
2. At the Proxmox VE boot menu, select **Install Proxmox VE**.  
3. Follow the installation wizard:  
   - Accept the license agreement.  
   - Select the target disk for installation.  
   - Configure the country, time zone, and keyboard layout.  
   - Set the administrator password and email.  
   - Configure the network settings (hostname, IP address, etc.).  

For more details, see the [Proxmox VE Administration Guide](https://pve.proxmox.com/pve-docs/pve-admin-guide.html).

---
### 3. Post-Installation Configuration  
1. After installation, remove the USB drive and reboot the server.  
2. Access the Proxmox web interface:  
   - Open a web browser and navigate to `https://<server-ip>:8006`.  
   - Log in using the `root` user and the password set during installation.  
3. Update the system:  
   - Ensure all packages are up-to-date.
   ```bash
   apt update && apt full-upgrade
   ```
4. Verify the installation and explore the interface.
5. (Optional) Add or configure additional storage as needed.  

For guidance on storage configuration, consult the [Proxmox VE Storage Documentation](https://pve.proxmox.com/pve-docs/chapter-pvesm.html).

---

## Next Steps
- Set up networking as detailed in the [Proxmox Networking Guide](docs/how-tos/0002_proxmox-networking.md).  
- Explore creating and managing virtual machines and containers.  
- Consider setting up backups and monitoring for your Proxmox VE environment.

For comprehensive documentation, visit the [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/).

By following this guide and utilizing the provided resources, you can effectively set up and manage your Proxmox VE 8.3 environment.
