# Ansible Role: adguardhome

Install [AdGuard Home](https://adguard.com/en/adguard-home/overview.html)

## Requirements
* Docker daemon and Docker SDK for Python is required on target host if **docker** install method selected (see Role variables section below)
* Snapd daemon is required on target host if **snap** install method selected (see Role variables section below)

## Role Variables
Variables with default values from [defaults/main.yml](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/adguardhome/defaults/main.yml)
```yaml
# Common vars
adguardhome_home: /opt/AdGuardHome
adguardhome_version: latest  # version to install
adguardhome_install_method: docker  # possible values binary, docker, snap
adguardhome_listen_all: true  # prepare system to allow AdGuard Home listen on all interfaces

# Binary relates vars
adguardhome_system_arch: amd64  # target system architecture. possible values 386, amd64, arm64,armv5, armv6, armv7
adguardhome_archive_name: 'AdGuardHome_linux_{{ adguardhome_system_arch }}.tar.gz'
adguardhome_bin_path: '{{ adguardhome_home }}/AdGuardHome'

# Docker related vars
adguardhome_docker_image: adguard/adguardhome
adguardhome_docker_hosts:
  - ['{{ ansible_fqdn }}', '{{ ansible_default_ipv4.address }}']  # add target host fqdn name to container's /etc/hosts
adguardhome_docker_labels: {}  # dict of container's labels
adguardhome_docker_mounts:
  - '{{ adguardhome_home }}/conf:/opt/adguardhome/conf'
  - '{{ adguardhome_home }}/work:/opt/adguardhome/work'
adguardhome_docker_network: bridge  # docker network to attach to container
adguardhome_docker_ports:  # list of port mappings
  - 53:53/tcp
  - 53:53/udp
  - 3000:3000/tcp

# Snap related vars
adguardhome_snap_channel: latest/stable  # channel to install from snap
```

## Example Playbook
```yaml
- name: Install AdGuard Home binary to host
  hosts: all
  roles:
    - bonddim.linux.adguard

- name: Install AdGuard Home docker container
  hosts: all
  vars:
    adguardhome_install_method: docker
  roles:
    - bonddim.linux.adguard

- name: Install AdGuard Home snap
  hosts: all
  vars:
    adguardhome_install_method: snap
  roles:
    - bonddim.linux.snapd
    - bonddim.linux.adguard
```
