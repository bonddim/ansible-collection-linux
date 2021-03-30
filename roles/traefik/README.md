# Ansible Role: traefik

[![Ansible Role](https://img.shields.io/ansible/role/51648?label=galaxy&logo=ansible)](https://galaxy.ansible.com/bonddim/traefik)
[![Ansible Role Downloads](https://img.shields.io/ansible/role/d/51648?logo=ansible)](https://galaxy.ansible.com/bonddim/traefik)
[![Ansible Quality Score](https://img.shields.io/ansible/quality/51648?logo=ansible)](https://galaxy.ansible.com/bonddim/traefik)
[![Workflow](https://img.shields.io/github/workflow/status/bonddim/ansible-role-traefik/Molecule?logo=github)](https://github.com/bonddim/ansible-role-traefik/actions)
[![License](https://img.shields.io/github/license/bonddim/ansible-role-traefik)](https://github.com/bonddim/ansible-role-traefik/blob/main/LICENSE)


Deploy and configure [Traefik v2](https://doc.traefik.io/traefik/)

Clean role execution will give you:
  - running traefik instance on 80 port
  - enabled traefik dashboard secured with basic authentication
  - security options for https with **A+** rate on [SSL Labs](https://www.ssllabs.com/ssltest/analyze.htm)

## Requirements
Docker daemon and Docker SDK for Python is required on target host if **docker** install method selected (see [variables](#role-variables) section)

## Role Variables
Variables with default values from [defaults/main.yml](https://github.com/bonddim/ansible-role-traefik/blob/main/defaults/main.yml)
```yaml
# Common vars
traefik_version: latest  # version to install, ex. v2.3.4
traefik_install_method: binary   # possible values: binary, docker
traefik_host_domainname: ""  # your domain name
traefik_env: {}  # dict with environment variables, mostly used for acme dns provider settings

# Container related vars
traefik_docker_network: bridge  # docker network name for traefik proxy

# Dashboard
traefik_dashboard_enable: true  # enable/disable dashboard
traefik_dashboard_middlewares: auth-basic@file  # apply middlewares for dashboard

# Basic auth
traefik_basic_auth_user: admin  # user name for basic auth
traefik_basic_auth_pass: $apr1$MR6nE9XC$lC2fnUmGLmsZDGqNlcdxU0  # password for basic auth generated with htpasswd (admin)

# Logs
traefik_log_level: ERROR  # traefik log level
traefik_log_format: json  # traefik log format
traefik_log_filepath: ""  # traefik log file path. Stdout is used when omitted or empty

# HTTPS
traefik_enable_https: false  # enable/disable https entrypoint
traefik_enable_https_redirect: true  # create permanent redirect from http to https

# ACME (Let's Encrypt) https://doc.traefik.io/traefik/https/acme
traefik_acme_enable: true  # enable/disable ACME resolver for HTTPS by default
traefik_acme_email: ""  # email for acme registration
traefik_acme_domains:
  - main: "{{ traefik_host_domainname }}"
    sans: ["*.{{ traefik_host_domainname }}"]
traefik_acme_challenge: dns  # possible values: dns, tls, http
traefik_acme_dns_provider: ""  # your dns provider
traefik_acme_dns_disablepropagationcheck: false  # Disable the DNS propagation checks before notifying ACME that the DNS challenge is ready. [not recommended]. When set to true it helps to get certs with dnsChallenge on gcloud and duckdns.org
traefik_acme_staging: false  # enable staging server for debug

# Providers
traefik_provider_docker: false  # enable/disable docker provider
traefik_provider_docker_exposebydefault: false  # enable/disable expose by default
traefik_provider_docker_defaultrule: ""  # default rule for docker provider
traefik_provider_docker_endpoint: ""  # default docker endpoint unix:///var/run/docker.sock

# Custom dynamic config
traefik_custom_config: {}  # Refer to traefik docs https://doc.traefik.io/traefik/reference/dynamic-configuration/file
```
Variables with default values from [vars/main.yml](https://github.com/bonddim/ansible-role-traefik/blob/main/vars/main.yml)

These are the preferred values, use extra-vars to override ([ansible docs](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable))
```yaml
traefik_user: traefik
traefik_group: '{{ traefik_user }}'

traefik_bin_path: /usr/local/bin/traefik
traefik_home: /etc/traefik
traefik_configfile_static: '{{ traefik_home }}/traefik.yaml'
traefik_configdir_dynamic: '{{ traefik_home }}/conf.d'
traefik_acme_storage_file: '{{ traefik_home }}/acme.json'
```

## Example Playbook
```yaml
- name: minimal setup with http
  hosts: all
  roles:
    - bonddim.traefik

- name: deploy traefik container and enable docker provider
  hosts: all
  vars:
    traefik_install_method: docker
    traefik_provider_docker: true
  roles:
    - bonddim.traefik

- name: enable docker provider with tcp endpoint to docker socket
  hosts: all
  vars:
    traefik_provider_docker: true
    traefik_provider_docker_endpoint: "tcp://host:port"
  roles:
    - bonddim.traefik

- name: minimal setup with https
  hosts: all
  vars:
    traefik_enable_https: true
    traefik_acme_email: email@example.com
    traefik_host_domainname: example.com
    traefik_acme_dns_provider: duckdns
    traefik_env:
      DUCKDNS_TOKEN: "duckdns_token_value"
  roles:
    - bonddim.traefik
```
See my [home-server](https://github.com/bonddim/home-server) playbooks for real use examples

## License
MIT

## Author Information
[Dmytro Bondar](https://github.com/bonddim)
