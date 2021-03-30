Ansible Role: snapd
=============

[![Ansible Role](https://img.shields.io/ansible/role/50784?label=galaxy&logo=ansible)](https://galaxy.ansible.com/bonddim/snapd)
[![Ansible Role Downloads](https://img.shields.io/ansible/role/d/50784?logo=ansible)](https://galaxy.ansible.com/bonddim/snapd)
[![Ansible Quality Score](https://img.shields.io/ansible/quality/50784?logo=ansible)](https://galaxy.ansible.com/bonddim/snapd)
[![Workflow](https://img.shields.io/github/workflow/status/bonddim/ansible-role-snapd/Molecule?logo=github)](https://github.com/bonddim/ansible-role-snapd/actions)
[![License](https://img.shields.io/github/license/bonddim/ansible-role-snapd)](https://github.com/bonddim/ansible-role-snapd/blob/main/LICENSE)

Install snap core and packages from https://snapcraft.io/store

Supported platforms
------------
  - Debian based distributions
  - CentOS 7/8
  - Fedora 31/32/33

Requirements
------------
Uses ansible [snap module](https://docs.ansible.com/ansible/latest/modules/snap_module.html) to install packages from snap store

Dependencies
------------
None

Role Variables
--------------
`snap_packages` - optional list of packages to install from snap-store
```yaml
snap_packages:
  - snap-store
  - name: code
    classic: true # optional. default is false
    channel: stable # optional. default is stable
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: bonddim.snap
      snap_packages:
        - skype
        - name: code
          classic: true
        - name: chromium
          channel: edge
```

License
-------
MIT

Author Information
------------------
[Dmytro Bondar](https://github.com/bonddim)
