# Ansible Role: bonddim.linux.epel

Install Extra Packages for Enterprise Linux (EPEL)<br>
Based on installation istructions from [Fedora](https://fedoraproject.org/wiki/EPEL) and [AWS](https://aws.amazon.com/premiumsupport/knowledge-center/ec2-enable-epel/)

## Supported platforms
* Amazon Linux 2
* AlmaLinux
* CentOs
* RockyLinux
* other RHEL based (not tested)


## Role Variables
```yaml
epel_package: 'https://dl.fedoraproject.org/pub/epel/epel-release-latest-{{ ansible_distribution_major_version }}.noarch.rpm'
```

## Example Playbook
```yaml
- hosts: rhel
  roles:
    - bonddim.linux.epel
```
