# ansible-role-git-lfs

[![Build Status](https://travis-ci.com/diodonfrost/ansible-role-git-lfs.svg?branch=master)](https://travis-ci.com/diodonfrost/ansible-role-git-lfs)
[![Molecule](https://github.com/diodonfrost/ansible-role-git-lfs/workflows/Molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-git-lfs/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.git_lfs-660198.svg)](https://galaxy.ansible.com/diodonfrost/git-lfs)

This role provide a compliance for install git-lfs on your target host.

## Requirements

This role was developed using Ansible 2.5 Backwards compatibility is not guaranteed.
Use `ansible-galaxy install diodonfrost.git_lfs` to install the role on your system.
*   Ansible >= 2.8
*   Python >= 2.7

Supported platforms:

```yaml
- name: EL
  versions:
    - 8
    - 7
    - 6
- name: Fedora
  versions:
    - 32
    - 31
    - 30
    - 29
    - 28
    - 27
    - 26
- name: Debian
  versions:
    - buster
    - stretch
    - jessie
- name: Ubuntu
  versions:
    - disco
    - bionic
    - xenial
    - trusty
- name: OracleLinux
  versions:
    - 8
    - 7
    - 6
- name: Amazon
  versions:
    - 2017.12
    - 2016.03
- name: ArchLinux
  versions:
    - any
- name: Alpine
  versions:
    - any
- name: Gentoo
  versions:
    - stage3
- name: FreeBSD
  versions:
    - 11.0
    - 12.0
- name: OpenBSD
  versions:
    - 6.0
- name: MacOSX
  versions:
    - 10.14
    - 10.15
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy diodonfrost.git_lfs role in a localhost and installing the latest version of git-lfs.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.git_lfs
```

## Local Testing

The preferred way of locally testing the role is to use Docker with Molecule. You will have to install Docker and Molecule on your system.

### Testing with Docker

```shell
# Test ansible role with centos-8
distribution=centos-8 molecule test

# Test ansible role with ubuntu-20.04
distribution=ubuntu-20.04 molecule test

# Test ansible role with alpine-rolling
distribution=alpine-rolling molecule test

# Create centos-7 instance
distribution=centos-7 molecule create

# Apply role on centos-7 instance
distribution=centos-7 molecule converge

# Launch tests on centos-7 instance
distribution=centos-7 molecule verify
```

### Testing with Vagrant and Virtualbox

```shell
# Test ansible role with FreeBSD
molecule test -s freebsd

# Test ansible role with OpenBSD
molecule test -s openbsd
```

## License

Apache 2

## Author Information

This role was created in 2020 by diodonfrost.
