ansible-role-git-lfs
====================

[![molecule](https://github.com/diodonfrost/ansible-role-git-lfs/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-git-lfs/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.git_lfs-660198.svg)](https://galaxy.ansible.com/diodonfrost/git-lfs)

Ansible role to install and initialize [Git LFS](https://git-lfs.com/) on a
wide range of operating systems. Packages come from the target OS package
manager (apt, dnf/yum, pacman, apk, emerge, pkg, homebrew) except on Windows,
where the official installer is fetched from the Git LFS GitHub releases.

Install with `ansible-galaxy install diodonfrost.git_lfs`.

Role Variables
--------------

The role picks the Git LFS package name per OS family from `vars/`. It exposes
a single variable, which can be overridden to target a different package or
slot:

| Variable | Description | Default |
|----------|-------------|---------|
| `git_lfs_package` | Name of the Git LFS package installed by the target OS package manager. Ignored on Windows (installer pulled from GitHub releases). | `git-lfs` (Linux / macOS), `devel/git-lfs` (FreeBSD), `dev-vcs/git-lfs` (Gentoo) |

After installation the role runs `git lfs install` globally only when
`filter.lfs.required` is not already present in the global git config — so the
role is idempotent across re-runs.

Dependencies
------------

This role depends on the following Ansible collections:
- `community.general` (for `git_config_info`, `homebrew`)
- `ansible.windows` (for the Windows installation path)

Example Playbook
----------------

Basic usage:

```yaml
- hosts: servers
  become: true
  roles:
    - role: diodonfrost.git_lfs
```

Overriding the package name (e.g., to install from a custom repository):

```yaml
- hosts: servers
  become: true
  roles:
    - role: diodonfrost.git_lfs
      vars:
        git_lfs_package: git-lfs-custom
```

Local Testing
-------------

This project uses [Molecule](https://ansible.readthedocs.io/projects/molecule/)
to aid in the development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](https://ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including `pip`)
* [Ansible](https://www.ansible.com/)
* [Molecule](https://ansible.readthedocs.io/projects/molecule/)
* [libvirt](https://libvirt.org/) (if you test a system other than Linux)
* [Vagrant](https://developer.hashicorp.com/vagrant/downloads) (if you test a system other than Linux)

Testing with Docker
-------------------

The `default` Molecule scenario is parameterized by two environment variables
matching how CI drives the matrix:

* `namespace` — container image registry / namespace (default: `diodonfrost`; CI uses `ghcr.io/diodonfrost`)
* `image`     — image name and tag (default: `ansible-ubuntu:24.04`)

Images are pulled from [`ghcr.io/diodonfrost/ansible-*`](https://github.com/diodonfrost?tab=packages).

```shell
# Install requirements
pip install -r requirements-dev.txt

# Full lifecycle against a CI image
image=ansible-debian:12 molecule test

# Other examples from the CI matrix
image=ansible-rockylinux:9 molecule test
image=ansible-fedora:43 molecule test
image=ansible-alpine:latest molecule test

# Iterate without tearing down
image=ansible-alpine:latest molecule create
image=ansible-alpine:latest molecule converge
image=ansible-alpine:latest molecule verify

# Check mode (dry-run) — CI runs this after `molecule test`
image=ansible-debian:12 molecule check
```

Testing with Vagrant and Libvirt
--------------------------------

```shell
# Test ansible role with Linux (Ubuntu 22.04)
molecule test -s linux

# Test ansible role with FreeBSD
molecule test -s freebsd

# Test ansible role with OpenBSD
molecule test -s openbsd

# Test ansible role with Windows
molecule test -s windows
```

License
-------

Apache Software License 2.0

Author Information
------------------

This role was created in 2020 by diodonfrost.
