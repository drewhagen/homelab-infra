
# NixOS Configuration Guide

## Overview
This guide explains how to configure a NixOS system declaratively using `configuration.nix`.

---

## Structure of `configuration.nix`
The main file (`/etc/nixos/configuration.nix`) defines the system's configuration.

---

## Example Configuration

### Basic Setup
```nix
{
  networking = {
    hostName = "nixos-vm";
    interfaces.eth0.ipv4.addresses = [{
      address = "192.168.1.101";
      prefixLength = 24;
    }];
    defaultGateway = "192.168.1.1";
  };

  services.sshd.enable = true;
  users.users.admin = {
    isNormalUser = true;
    extraGroups = [ "wheel" ];
  };
}
```

---

### Managing Packages
```nix
{
  environment.systemPackages = with pkgs; [
    vim
    htop
    git
  ];
}
```

---

## Applying Changes
1. Save changes to `/etc/nixos/configuration.nix`.
2. Rebuild and apply:
   ```bash
   nixos-rebuild switch
   ```

---

