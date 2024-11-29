# 3. Use NixOS to Configure the Proxmox Host

## Context
The Proxmox host needs an operating system to manage its services and configurations. We want:
- A declarative approach to configuration management.
- The ability to perform atomic updates and rollbacks.
- High reproducibility and consistency.

## Decision
We will use **NixOS** as the operating system for the Proxmox host.

## Rationale
1. **Declarative Configuration**:
   - NixOS allows all configurations (e.g., networking, storage, users) to be defined in a single source of truth.
2. **Atomic Upgrades and Rollbacks**:
   - NixOS provides a robust mechanism for upgrading or reverting configurations safely.
3. **Reproducibility**:
   - The declarative nature of NixOS ensures the Proxmox host can be rebuilt exactly as configured.
4. **Community Support**:
   - While Proxmox on NixOS is not as common as Debian-based setups, tools like `proxmox-nixos` simplify integration.

## Consequences
- The Proxmox host will use NixOS instead of the default Debian-based OS.
- Custom NixOS configurations will be required to enable Proxmox services.
- Team members must be comfortable with the Nix language and ecosystem.
