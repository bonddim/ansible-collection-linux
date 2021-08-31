# Ansible Role: snapd

Install snap core and packages from https://snapcraft.io/store

## Supported platforms
* Debian based distributions
* CentOS 7/8
* Fedora
* Amazon Linux 2

## Role Variables
```yaml
snap_packages: []  # optional list of packages to install from snap-store
```

## Example Playbook
```yaml
- hosts: servers
  roles:
    - role: bonddim.linux.snapd
      snap_packages:
        - skype
        - name: code
          classic: true  # optional. default is false
        - name: chromium
          channel: edge  # optional. default is stable
```
