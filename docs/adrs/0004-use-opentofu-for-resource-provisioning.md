# 4. Use Terraform/OpenTofu for Resource Provisioning

## Context
We need a tool to provision and manage resources (VMs, containers, networks) declaratively in Proxmox. The tool must:
- Be well-supported and mature.
- Integrate with Proxmox’s API.
- Enable version control and automation.

## Decision
We will use **Terraform (or OpenTofu)** with the Proxmox provider for resource provisioning.

## Rationale
1. **Declarative Infrastructure**:
   - Terraform allows us to define resources as code, making them version-controlled and reproducible.
2. **Proxmox Integration**:
   - The Proxmox provider supports VM, storage, and network management.
3. **Ecosystem**:
   - Terraform/OpenTofu is widely adopted, with strong community and tool support.
4. **Future-Readiness**:
   - Terraform enables integration with other cloud providers, supporting potential hybrid setups.

## Consequences
- Resource provisioning will depend on Terraform configurations stored in the monorepo.
- Changes to infrastructure must follow a plan/apply workflow.
- The team must maintain Terraform versions compatible with the Proxmox provider.
