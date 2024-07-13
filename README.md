# Ansible role [docker](https://galaxy.ansible.com/ui/standalone/roles/buluma/docker/documentation)

Install and configure Docker (non-CE) on your system.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-docker/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-docker/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-docker.svg)](https://github.com/buluma/ansible-role-docker/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-docker.svg)](https://github.com/buluma/ansible-role-docker/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-docker.svg)](https://github.com/buluma/ansible-role-docker/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/docker)](https://galaxy.ansible.com/ui/standalone/roles/buluma/docker/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-docker/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: buluma.docker
      docker_privileged_users:
        - woody
        - buzz

  tasks:
    - name: Create test case users
      ansible.builtin.user:
        name: "{{ user }}"
      loop:
        - woody
        - buzz
      loop_control:
        loop_var: user
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-docker/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: false

  roles:
    - role: buluma.bootstrap
    - role: buluma.core_dependencies
    - role: buluma.buildtools
    - role: buluma.epel
    - role: buluma.python_pip
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-docker/blob/master/defaults/main.yml):

```yaml
---
# defaults file for docker

# Add users to the privileged docker group. For example:
# docker_privileged_users:
#   - UserA
#   - UserB
docker_privileged_users: []
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-docker/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.buildtools](https://galaxy.ansible.com/buluma/buildtools)|[![Ansible Molecule](https://github.com/buluma/ansible-role-buildtools/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-buildtools/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-buildtools.svg)](https://github.com/shadowwalker/ansible-role-buildtools)|
|[buluma.core_dependencies](https://galaxy.ansible.com/buluma/core_dependencies)|[![Ansible Molecule](https://github.com/buluma/ansible-role-core_dependencies/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-core_dependencies/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-core_dependencies.svg)](https://github.com/shadowwalker/ansible-role-core_dependencies)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Ansible Molecule](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-epel.svg)](https://github.com/shadowwalker/ansible-role-epel)|
|[buluma.python_pip](https://galaxy.ansible.com/buluma/python_pip)|[![Ansible Molecule](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-python_pip.svg)](https://github.com/shadowwalker/ansible-role-python_pip)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-docker/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|focal, bionic, jammy, noble|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-docker/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-docker/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-docker/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)
