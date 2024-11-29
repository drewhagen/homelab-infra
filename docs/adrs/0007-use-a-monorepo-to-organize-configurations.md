# 7. Use a Monorepo to Organize Configurations

## Context
The homelab includes multiple tightly integrated tools (Proxmox, Ansible, Kubernetes). We need a way to:
- Manage configurations and scripts for these tools.
- Ensure consistency and simplicity.

## Decision
We will use a **monorepo** to organize configurations for the homelab.

## Rationale
1. **Centralization**:
   - All configurations are stored in one place, simplifying cross-tool integration.
2. **Ease of Use**:
   - A single repository is easier to clone, manage, and document for small-scale setups.
3. **Simplicity**:
   - Shared scripts and CI/CD pipelines can be managed centrally.
4. **Future Growth**:
   - The monorepo structure can evolve into a multi-repo if the project grows in complexity.

## Consequences
- All configurations and documentation will be maintained in the monorepo.
- Modular subdirectories will separate concerns (e.g., Proxmox, Kubernetes).
- CI/CD pipelines will need to support cross-tool workflows.
