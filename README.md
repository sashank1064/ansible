# ansible

> A progressive walk-through of Ansible fundamentals — from ad-hoc commands to roles, handlers, vaults, and dynamic inventory.

![Ansible](https://img.shields.io/badge/Ansible-EE0000?logo=ansible&logoColor=white)
![YAML](https://img.shields.io/badge/YAML-CB171E?logo=yaml&logoColor=white)
![Jinja](https://img.shields.io/badge/Jinja2-B41717?logo=jinja&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?logo=amazonaws&logoColor=white)

## What this is

A reference workspace for learning and practicing **Ansible** end-to-end. Each top-level directory covers one concept in isolation with a small, runnable example — so I can look up the minimum working version of any pattern (`loop`, `block/rescue/always`, `vault`, `dynamic inventory`, `handlers`, `tags`, etc.) instead of hunting through StackOverflow.

Consider this the "textbook" repo. The real projects that apply these patterns are:

- [`ansible-roboshop`](https://github.com/sashank1064/ansible-roboshop) — flat playbooks on an 11-service app
- [`ansible-roboshop-roles`](https://github.com/sashank1064/ansible-roboshop-roles) — refactored into reusable roles

## Topics covered

| Topic | What's inside |
|---|---|
| **Ad-hoc commands** | `ansible -m ping`, `-m command`, `-m shell` against EC2 hosts |
| **Playbooks** | `tasks`, `vars`, `when`, `loop`, `notify` |
| **Handlers** | Restart-on-change pattern with `notify` + `listen` |
| **Variables &amp; precedence** | `defaults/` < `group_vars/` < `host_vars/` < extra-vars |
| **Templates** | Jinja2 rendering of config files |
| **Conditionals &amp; loops** | `when`, `with_items`, `loop`, `with_nested` |
| **Error handling** | `block/rescue/always`, `failed_when`, `ignore_errors` |
| **Roles** | Role skeleton, `meta/dependencies`, Galaxy |
| **Vault** | `ansible-vault encrypt`, vault-id per environment |
| **Dynamic inventory** | AWS EC2 plugin with tag-based groups |
| **Tags** | Selective execution with `--tags` / `--skip-tags` |

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

## Why maintain a learning repo

Three reasons:

1. **Muscle memory.** Writing the skeleton from scratch is faster than copying from docs once the patterns stick.
2. **Onboarding teammates.** When someone new joins and asks "how do handlers actually work?" I send them a 20-line example, not a 400-line production role.
3. **Interview prep.** Every pattern here has been asked about in at least one interview loop.

---

Part of my DevOps portfolio.
