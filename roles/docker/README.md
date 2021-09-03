# Ansible Role: bonddim.linux.docker

Install Docker Engine and optionally docker-compose binary<br>
Based on installation istructions from official [docs](https://docs.docker.com/engine/install/)

## Supported platforms

- AlmaLinux
- Amazon Linux
- Amazon Linux 2
- CentOS
- Debian
- Fedora
- RHEL
- Rocky Linux
- Ubuntu

## Role Variables

Variables with default values from [defaults/main.yml](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/docker/defaults/main.yml)

```yaml
docker_system_arch: amd64 # default target system arch
docker_daemon_state: started # daemon state after role execution
docker_daemon_enable: true # enable docker daemon on system startup
docker_package_state: present # use latest to update installed docker
docker_users: [] # list of users to add to docker group

# docker-compose
docker_compose_install: false # install docker-compose
docker_compose_install_path: /usr/local/bin/docker-compose # docker-compose binary install path
docker_compose_version: latest # docker-compose version to install
```

Variables with default values from [vars/main.yml](https://github.com/bonddim/ansible-collection-linux/blob/main/roles/docker/vars/main.yml)<br>
These are the preferred values, use extra-vars to override ([ansible docs](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable))

```yaml
docker_download_url: 'https://download.docker.com/linux'
docker_base_url: '{{ docker_download_url }}/{{ ansible_distribution | lower }}'
docker_packages:
  - docker-ce
  - docker-ce-cli
  - containerd.io
```

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: bonddim.linux.docker
      docker_users:
        - user1
        - user2
```
