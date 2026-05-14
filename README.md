# Homelab

<!-- RU: Это мой домашний инфраструктурный репозиторий. Всё, что я создаю в лабе, описывается здесь как код или документация. -->

My personal homelab infrastructure as code. Everything I build in my lab —
VMs, containers, network config, services — is tracked here.

## Goals

- Practice Infrastructure as Code (Terraform/OpenTofu + Ansible)
- Build a reproducible, documented home environment
- Learn SRE / platform engineering practices on real hardware

## Hardware

See [`docs/inventory.md`](docs/inventory.md) for the full hardware list and
current VM layout.

Currently running:

- **n5** — Minisforum N5, Proxmox VE hypervisor
- **pbs** (VM on n5) — Proxmox Backup Server

## Repository layout

```
homelab/
├── docs/         # Documentation: inventory, network, runbooks, decisions
├── ansible/      # Ansible playbooks and roles (configuration management)
├── terraform/    # Terraform / OpenTofu code (resource provisioning) — TBD
└── k8s/          # Kubernetes manifests — TBD
```

<!-- RU: ansible настраивает уже существующие машины. terraform создаёт сами машины. docs — память. -->

## Status

This is an active learning project. Expect things to change, break, and get
rewritten. See [`docs/decisions/`](docs/decisions/) for the reasoning behind
architectural choices.

## Conventions

- All code and docs are in **English** (with occasional Russian comments
  marked `<!-- RU: ... -->` for my own notes).
- **No secrets in Git.** Ever. See [`.gitignore`](.gitignore).
- Commits follow the format: `area: short description`
  (e.g. `ansible: add docker role`, `docs: update inventory`).

## License

Personal project, no license — code is provided as reference only.
