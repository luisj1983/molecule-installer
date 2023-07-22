# RedHat Ansible Molecule installer (WSL and native)

[![ansible-lint](https://github.com/luisj1983/molecule-installer/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/luisj1983/molecule-installer/actions/workflows/ansible-lint.yml)

# Summary

This playbook will install Ansible Molecule and any pre-requisites required for use with Docker, as well as Docker itself.

It is designed to be executed on the Ansible Control Node and will make all changes **locally**.

It is expected to work on `Ubuntu 18.xx` onwards and, potentially, `Debian 10` onwards.

Invoke using:

> ansible-playbook -K molecule_installer.yml

# Included tasks: pre-requisites
- `Enable systemd for WSL2`
- `Delete any existing Docker config/keys from apt`
- `Install Docker-ce and docker-compose from Docker.com repository`
- `Install Docker Module for Python`
- `Ensure group "docker" exists`
- `Added user to docker group`
- `Group change notification (notify user to run newgrp for group-permissions to take effect)`

# Included tasks: Molecule
- `Install Molecule pre-reqs` (Python3 and libssl)
- `Install/upgrade setuptools`
- `Install Molecule`
- `Install/upgrade setuptools`
- `Install/upgrade ansible-lint`
- `Install Molecule Docker`
- `Install Molecule Docker Driver`

# Notes

`/vars/main.yml` contains a mapping lookup for `ansible_distribution_file_variety` and `ansible_architecture` to construct the correct Docker repository URI.

# To do

- [ ] Make playbook support additional Operating Systems (e.g. CentOS)
- [ ] Break out sub-tasks such as docker_install, ansible_install

## License
GPL-3.0-or-later
