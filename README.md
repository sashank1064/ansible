# ansible

A patterns reference for Ansible: ad-hoc commands, playbooks, roles, handlers, vault, dynamic inventory. Each topic has a small, runnable example.

![Ansible](https://img.shields.io/badge/Ansible-EE0000?logo=ansible&logoColor=white)
![YAML](https://img.shields.io/badge/YAML-CB171E?logo=yaml&logoColor=white)
![Jinja](https://img.shields.io/badge/Jinja2-B41717?logo=jinja&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?logo=amazonaws&logoColor=white)

## Overview

A reference workspace for Ansible patterns. Each top-level directory covers one concept in isolation with a minimal runnable example: loops, block/rescue/always, vault, dynamic inventory, handlers, tags, and so on.

For the real projects that apply these patterns at scale, see:

- [`ansible-roboshop`](https://github.com/sashank1064/ansible-roboshop): flat playbooks on an 11-service app
- [`ansible-roboshop-roles`](https://github.com/sashank1064/ansible-roboshop-roles): refactored into reusable roles

## Topics

| Topic | What's inside |
|---|---|
| Ad-hoc commands | `ansible -m ping`, `-m command`, `-m shell` against EC2 hosts |
| Playbooks | `tasks`, `vars`, `when`, `loop`, `notify` |
| Handlers | Restart-on-change with `notify` and `listen` |
| Variables &amp; precedence | `defaults/` < `group_vars/` < `host_vars/` < extra-vars |
| Templates | Jinja2 rendering of config files |
| Conditionals &amp; loops | `when`, `with_items`, `loop`, `with_nested` |
| Error handling | `block/rescue/always`, `failed_when`, `ignore_errors` |
| Roles | Role skeleton, `meta/dependencies`, Galaxy |
| Vault | `ansible-vault encrypt`, vault-id per environment |
| Dynamic inventory | AWS EC2 plugin with tag-based groups |
| Tags | Selective execution with `--tags` and `--skip-tags` |

## Repo layout

```
.
├── 01-adhoc/
├── 02-playbooks/
├── 03-variables/
├── 04-templates/
├── 05-conditionals-and-loops/
├── 06-handlers/
├── 07-error-handling/
├── 08-roles/
├── 09-vault/
├── 10-dynamic-inventory/
└── inventory.ini
```

Each numbered folder is independent. Open it, run the playbook, read the comments.

## Quick start

```bash
# Install Ansible locally
python3 -m pip install --user ansible

# Verify the inventory can reach your hosts
ansible -i inventory.ini all -m ping

# Run any topic folder's playbook
ansible-playbook -i inventory.ini 02-playbooks/install-nginx.yml
```
