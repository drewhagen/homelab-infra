# 5. Use Ansible for Post-Provisioning Configuration

## Context
After provisioning VMs and containers, they need to be configured with operating systems, applications, and users. This process must:
- Be automated and repeatable.
- Allow procedural tasks not suited to Terraform or NixOS.

## Decision
We will use **Ansible** for post-provisioning configuration.

## Rationale
1. **Automation**:
   - Ansible automates configuration tasks like installing software and setting up users.
2. **Flexibility**:
   - Ansible can handle tasks beyond declarative tools (e.g., installing specific package versions).
3. **Broad Support**:
   - Ansible supports most operating systems, making it suitable for various VMs and containers.
4. **Community**:
   - Ansible has a large community and extensive libraries for common tasks.

## Consequences
- Ansible playbooks and roles will be developed for configuring VMs and containers.
- Inventory files must be maintained to track hosts and their configurations.
- Changes to configurations must be applied using Ansible commands.
