# Ansible Role: lxd

[![Ansible Role](https://img.shields.io/ansible/role/51734?label=galaxy&logo=ansible)](https://galaxy.ansible.com/bonddim/lxd)
[![Ansible Role Downloads](https://img.shields.io/ansible/role/d/51734?logo=ansible)](https://galaxy.ansible.com/bonddim/lxd)
[![Ansible Quality Score](https://img.shields.io/ansible/quality/51734?logo=ansible)](https://galaxy.ansible.com/bonddim/lxd)
[![Workflow](https://img.shields.io/github/workflow/status/bonddim/ansible-role-lxd/Molecule?logo=github)](https://github.com/bonddim/ansible-role-lxd/actions)
[![License](https://img.shields.io/github/license/bonddim/ansible-role-lxd)](https://github.com/bonddim/ansible-role-lxd/blob/main/LICENSE)

## Features
* Install latest version of LXD from [Snapcraft](https://snapcraft.io/store)
* Migrate existing LXD configuration on Ubuntu systems

## Supported platforms
* Ubuntu
* Debian (may require restart)
* Centos
* Fedora

Check list of tested environments in [workflow](https://github.com/bonddim/ansible-role-lxd/blob/main/.github/workflows/molecule.yaml) file

## Dependencies
From [meta/main.yaml](https://github.com/bonddim/ansible-role-lxd/blob/main/meta/main.yml)
```yaml
dependencies:
  - role: bonddim.snapd
    snap_packages:
      - lxd
```

## Role Variables
Variables with default values from [defaults/main.yaml](https://github.com/bonddim/ansible-role-lxd/blob/main/defaults/main.yaml)
```yaml
lxd_users: []  # list of users to add to lxd group
```

## Example Playbook
```yaml
- hosts: servers
  roles:
    - role: bonddim.lxd
      lxd_users:
        - user1
        - user2
```

## License
MIT

## Author Information
[Dmytro Bondar](https://github.com/bonddim)
