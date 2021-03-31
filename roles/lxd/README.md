# Ansible Role: bonddim.linux.lxd

Install latest version of LXD from [Snapcraft](https://snapcraft.io/store)<br>
Migrate existing LXD configuration on Ubuntu systems

## Supported platforms
* Ubuntu
* Debian (may require restart)
* Centos
* Fedora

## Dependencies
From [meta/main.yaml](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/lxd/meta/main.yml)
```yaml
dependencies:
  - role: bonddim.linux.snapd
    snap_packages:
      - lxd
```

## Role Variables
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
