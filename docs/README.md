# Docs

<!-- RU: Папка с документацией. -->

Documentation hub for the lab.

| File / folder              | Purpose                                                   |
|----------------------------|-----------------------------------------------------------|
| `inventory.md`             | Hardware and VM list. Update on every change.             |
| `network.md`               | Network topology, IP plan, DNS.                           |
| `runbooks/`                | Step-by-step procedures: backup restore, host setup, etc. |
| `decisions/`               | ADRs — why I chose X over Y.                              |

## Writing new docs

- Use Markdown.
- Keep it short. A doc nobody reads is worse than no doc.
- Update `inventory.md` whenever you add or remove a VM/host.
- Add a runbook the **first time** you do something painful manually.
- Add an ADR when you make a non-obvious architectural choice.
