# ansible-role-git-lfs

[![molecule](https://github.com/diodonfrost/ansible-role-git-lfs/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-git-lfs/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.git_lfs-660198.svg)](https://galaxy.ansible.com/diodonfrost/git-lfs)

This role provide a compliance for install git-lfs on your target host.

## Requirements

This role was developed using Ansible 2.5 Backwards compatibility is not guaranteed.
Use `ansible-galaxy install diodonfrost.git_lfs` to install the role on your system.

* Ansible >= 2.11
* Python >= 2.7

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
- name: Windows
  versions:
    - 2016
    - 2012R2
    - 2008R2
    - 8.1
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

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Virtualbox](https://www.virtualbox.org/) (windows/bsd test only)
* [Vagrant](https://www.vagrantup.com/downloads.html) (windows/bsd test only)

### Testing with Docker

```shell
# Test ansible role with centos-8
image=ansible-centos:8 molecule test

# Test ansible role with ubuntu-20.04
image=ansible-ubuntu:20.04 molecule test

# Test ansible role with alpine-rolling
image=ansible-alpine:latest molecule test

# Create centos-7 instance
image=ansible-centos:7 molecule create

# Apply role on centos-7 instance
image=ansible-centos:7 molecule converge

# Launch tests on centos-7 instance
image=ansible-centos:7 molecule verify
```

### Testing with Vagrant and Virtualbox

```shell
# Test ansible role with FreeBSD
molecule test -s freebsd

# Test ansible role with OpenBSD
molecule test -s openbsd

# Test ansible role with Windows
molecule test -s windows
```

## License

Apache 2

## Author Information

This role was created in 2020 by diodonfrost.
