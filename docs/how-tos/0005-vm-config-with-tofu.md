
# VM Config using OpenTofu with Proxmox

## Overview
This guide explains how to provision and manage Proxmox VMs declaratively using Terraform/OpenTofu.

---

## Prerequisites
- Proxmox VE with API access enabled.
- Terraform/OpenTofu installed locally.

---

## Steps

### 1. Set Up the Proxmox Provider
1. Create a `main.tf` file:
   ```hcl
   provider "proxmox" {
     pm_api_url      = "https://<proxmox-ip>:8006/api2/json"
     pm_user         = "root@pam"
     pm_password     = "your-password"
     pm_tls_insecure = true
   }
   ```

---

### 2. Define a VM
1. Add a VM resource:
   ```hcl
   resource "proxmox_vm_qemu" "nixos_vm" {
     name   = "nixos-vm"
     cores  = 2
     memory = 2048
     network {
       model  = "virtio"
       bridge = "vmbr0"
     }
     disk {
       size = "20G"
       type = "scsi"
     }
   }
   ```

---

### 3. Apply the Configuration
1. Initialize Terraform:
   ```bash
   terraform init
   ```
2. Plan and apply:
   ```bash
   terraform plan
   terraform apply
   ```

---

## Next Steps
- Use Ansible to configure the VM (`docs/ansible-vm-config.md`).
