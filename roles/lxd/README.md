# Ansible Role: bonddim.linux.lxd

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
  - role: bonddim.linux.snapd
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
    - role: bonddim.linux.lxd
      lxd_users:
        - user1
        - user2
```
