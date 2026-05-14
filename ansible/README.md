# Ansible

<!-- RU: Ansible — настраивает уже существующие машины по SSH.
     Запускаешь playbook → он идёт на хосты из inventory и применяет роли. -->

Configuration management for hosts in this lab. Ansible connects over SSH
and brings each host to the desired state defined here.

## Layout

```
ansible/
├── inventory.yml      # List of hosts and groups
├── group_vars/        # Variables shared by host groups
├── host_vars/         # Variables specific to a single host
├── playbooks/         # Entry points: "what to run"
└── roles/             # Reusable units: "how to do one thing"
```

## Prerequisites

- Ansible installed on your control machine (laptop):
  ```
  pipx install ansible-core
  ```
- SSH key set up and copied to each managed host:
  ```
  ssh-copy-id user@host
  ```

## Running a playbook

Dry run (shows what would change, makes no changes):
```
ansible-playbook -i inventory.yml playbooks/base-setup.yml --check --diff
```

Real run:
```
ansible-playbook -i inventory.yml playbooks/base-setup.yml
```

Limit to one host:
```
ansible-playbook -i inventory.yml playbooks/base-setup.yml --limit pbs
```

## Conventions

- One role = one responsibility (`common`, `docker`, `node_exporter`, etc.).
- Variables live in `group_vars/` or `host_vars/`, never hardcoded in roles.
- Secrets go in `ansible-vault`-encrypted files, never in plain YAML.
