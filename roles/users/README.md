# Ansible Role: users

Manage Linux users and groups

## Supported platforms
Linux hosts

## Role Variables
```yaml
# list of groups to manage
managed_groups:
  - default_group  # Will be created with ansible defaults
  - name: system_group  # # See full list of arguments on https://docs.ansible.com/ansible/latest/collections/ansible/builtin/group_module.html
    system: true

# list of users to manage
managed_users:
  - default_user  # Will be created with ansible defaults
  - name: system_user  # See full list of arguments on https://docs.ansible.com/ansible/latest/collections/ansible/builtin/user_module.html
    system: true
    groups: [admin, system_group]
```

## Example Playbook
```yaml
- name: Create ansible system group and users with this group
  gather_facts: false
  roles:
    - role: bonddim.linux.users
      managed_groups:
        - name: ansible
          system: true
      managed_users:
        - name: ansible_admin
          groups: [ansible, admin]
          shell: /bin/bash
        - name: ansible_user
          groups: [ansible, users]
          shell: /bin/bash

- name: Create ansible system group and user without home directory
  hosts: all
  gather_facts: false
  roles:
    - role: bonddim.linux.users
      managed_users:
        - name: ansible
          system: true
          create_home: false
```
