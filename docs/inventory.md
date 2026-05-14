# Inventory

<!-- RU: Главный справочник по железу и VM. Обновляй каждый раз, когда что-то добавляешь или меняешь. -->

Single source of truth for hardware and virtual machines in this lab.
Update on every change.

## Physical hosts

| Hostname | Model              | CPU | RAM | Storage                                  | Mgmt IP        | Role            |
|----------|--------------------|-----|-----|------------------------------------------|----------------|-----------------|
| n5       | Minisforum N5      | TBD | TBD | 64GB SSD (system) + 500GB SSD (VM store) | 192.168.1.10   | Proxmox VE host |

<!-- RU: TBD = to be determined. Заполню, когда уточню точные характеристики. -->

## Virtual machines on `n5`

| VMID | Name | OS                     | vCPU | RAM   | Disk             | IP             | Purpose         |
|------|------|------------------------|------|-------|------------------|----------------|-----------------|
| 100  | pbs  | Proxmox Backup Server  | 2    | 2 GB  | 32 GB + 250 GB   | 192.168.1.11   | Backup target   |

## Planned

- **truenas** (VM on n5) — TrueNAS Scale, NFS/SMB storage. Waiting for disks.
- **k3s-1..3** — Kubernetes cluster nodes (LXC or VMs, TBD).

## Network

| Subnet           | Purpose                         | Gateway       | Notes                  |
|------------------|---------------------------------|---------------|------------------------|
| 192.168.1.0/24   | Flat LAN (current)              | 192.168.1.1   | GL.iNet Slate7 router  |

<!-- RU: VLAN-сегментация — позже. Пока всё в одной плоской сети. -->

## Credentials location

Credentials are **not** stored in Git. See `docs/runbooks/credentials.md`
(local-only, gitignored) for where passwords and tokens live.
