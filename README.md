# Ansible Collection - bonddim.linux

[![Galaxy version](https://img.shields.io/badge/dynamic/json?style=flat&label=galaxy&logo=ansible&url=https://galaxy.ansible.com/api/v2/collections/bonddim/linux/&query=latest_version.version)](https://galaxy.ansible.com/bonddim/linux)
[![Licence](https://img.shields.io/github/license/bonddim/ansible-collection-linux?logo=license)](https://github.com/bonddim/ansible-collection-linux/blob/main/LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/bonddim/ansible-collection-linux?logo=github)](https://github.com/bonddim/ansible-collection-linux/commits/main)

## Tested with Ansible
Tested with the stable releases of Ansible 2.9, 2.10, 2.11, 2.12 on
  - almalinux/8
  - amazonlinux
  - centos/7
  - debian/11
  - fedora/35
  - oracle/8
  - rockylinux/8
  - ubuntu/20.04

## Dependencies
```yaml
collections:
  - name: community.general
  - name: community.docker
```


## Included content
### Roles

| FQDN Name | Documentation | Build Status |
| --------- | :-----------: | :----------: |
| bonddim.linux.adguardhome | [Readme](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/adguardhome/README.md) | [![](https://img.shields.io/github/workflow/status/bonddim/ansible-collection-linux/adguardhome/main?logo=github)](https://github.com/bonddim/ansible-collection-linux/actions/workflows/role_adguardhome.yaml?query=branch%3Amain) |
| bonddim.linux.docker | [Readme](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/docker/README.md) | [![](https://img.shields.io/github/workflow/status/bonddim/ansible-collection-linux/docker/main?logo=github)](https://github.com/bonddim/ansible-collection-linux/actions/workflows/role_docker.yaml?query=branch%3Amain) |
| bonddim.linux.epel | [Readme](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/epel/README.md) | [![](https://img.shields.io/github/workflow/status/bonddim/ansible-collection-linux/epel/main?logo=github)](https://github.com/bonddim/ansible-collection-linux/actions/workflows/role_epel.yaml?query=branch%3Amain) |
| bonddim.linux.lxd | [Readme](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/lxd/README.md) | [![](https://img.shields.io/github/workflow/status/bonddim/ansible-collection-linux/lxd/main?logo=github)](https://github.com/bonddim/ansible-collection-linux/actions/workflows/role_lxd.yaml?query=branch%3Amain) |
| bonddim.linux.snapd | [Readme](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/snapd/README.md) | [![](https://img.shields.io/github/workflow/status/bonddim/ansible-collection-linux/snapd/main?logo=github)](https://github.com/bonddim/ansible-collection-linux/actions/workflows/role_snapd.yaml?query=branch%3Amain) |
| bonddim.linux.traefik | [Readme](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/traefik/README.md) | [![](https://img.shields.io/github/workflow/status/bonddim/ansible-collection-linux/traefik/main?logo=github)](https://github.com/bonddim/ansible-collection-linux/actions/workflows/role_traefik.yaml?query=branch%3Amain) |
| bonddim.linux.users | [Readme](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/users/README.md) | [![](https://img.shields.io/github/workflow/status/bonddim/ansible-collection-linux/users/main?logo=github)](https://github.com/bonddim/ansible-collection-linux/actions/workflows/role_users.yaml?query=branch%3Amain) |


## Using this collection
Before using the collection, you need to install the collection with the `ansible-galaxy` CLI:
```bash
ansible-galaxy collection install bonddim.linux
```

You can also include it in a `requirements.yml` file and install it via `ansible-galaxy collection install -r requirements.yml` using the format:
```yaml
collections:
  - bonddim.linux
```

See [Ansible Using collections](https://docs.ansible.com/ansible/latest/user_guide/collections_using.html) for more details.


## Contributing to this collection
If you want to develop new content for this collection or improve what is already here, please open an issue or create a PR


## More information
- [Ansible Collection overview](https://github.com/ansible-collections/overview)
- [Ansible User guide](https://docs.ansible.com/ansible/latest/user_guide/index.html)


## Licensing
GNU General Public License v3.0 or later

See [LICENSE](https://github.com/bonddim/ansible-collection-linux/blob/main/LICENSE) to see the full text.
