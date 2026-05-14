# ADR 0001: Use Proxmox VE as the hypervisor

<!-- RU: ADR = Architecture Decision Record. Короткая запись "что решил и почему".
     Через год сам себе скажешь спасибо, когда забудешь, почему выбрал именно это. -->

- **Status:** Accepted
- **Date:** 2026-05-13

## Context

I need a hypervisor for my homelab on a Minisforum N5. The hypervisor must
support running multiple VMs and LXC containers, allow backups, and be
manageable remotely. I also want to learn industry-relevant tools.

## Decision

Use **Proxmox VE** as the hypervisor on the N5.

## Alternatives considered

- **VMware ESXi free** — no longer freely available under sustainable terms
  for hobbyists after Broadcom's licensing changes.
- **XCP-ng** — solid, but smaller community and fewer tutorials than Proxmox.
- **Bare-metal Linux + KVM/libvirt** — more flexible, but I lose the web UI,
  built-in clustering, and backup integration. Higher learning curve for
  little gain at this stage.
- **TrueNAS Scale as hypervisor** — possible, but TrueNAS is storage-first;
  Proxmox is virtualization-first. I'll run TrueNAS as a VM on Proxmox instead.

## Consequences

- ✅ Strong community, many tutorials, active forum.
- ✅ Built-in support for LXC, ZFS, clustering, backups (via PBS).
- ✅ Web UI plus full CLI/API for automation later.
- ✅ Terraform provider available (`bpg/proxmox`) for IaC.
- ⚠️ Debian-based; security updates require attention.
- ⚠️ Enterprise repo requires a subscription; using the no-subscription repo
  is fine for a homelab but shows a nag dialog.
