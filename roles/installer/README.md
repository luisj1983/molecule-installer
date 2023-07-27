# RedHat Ansible Molecule installer (WSL and native)

[![ansible-lint](https://github.com/luisj1983/molecule-installer/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/luisj1983/molecule-installer/actions/workflows/ansible-lint.yml)

# Summary

This playbook will install Ansible Molecule and any pre-requisites required for use with Docker, as well as Docker itself.

It is designed to be executed on the Ansible Control Node and will make all changes **locally**.

It is expected to work on `Ubuntu 18.xx` onwards and, potentially, `Debian 10` onwards.

<br />

# Roles
## installer


### installer: Included tasks: installer_prep
- `Enable systemd for WSL2`

### installer: Included tasks: installer_docker
- `Delete any existing Docker config/keys from apt`
- `Install Docker-ce and docker-compose from Docker.com repository`
- `Install Docker Module for Python`
- `Ensure group "docker" exists`
- `Added user to docker group`
- `Group change notification (notify user to run newgrp for group-permissions to take effect)`

### installer: Included tasks: installer_ansible
- `Install ansible-core and ansible-lint using PIP`

### installer: Included tasks: installer_molecule
- `Install Molecule pre-reqs` (Python3 and libssl)
- `Install/upgrade setuptools`
- `Install Molecule`
- `Install/upgrade ansible-lint`
- `Install Molecule-Docker`
- `Install Molecule-Docker Driver`

# Usage

Invoke using:
```
ansible-playbook -K main.yml -tags <ROLENAME>
```
e.g.
```
ansible-playbook -K main.yml -tags installer
```
<br />


# Notes

1. `groupvars/main.yml` contains a mapping lookup for `ansible_distribution_file_variety` and `ansible_architecture` to construct the correct Docker repository URI.

2. `molecule_driver_cleanup` and `docker_cleanup_required` are set to `true` by default.<br />
The effect is that the playbook isn't, strictly speaking fully idempotent.<br />
However, since those tasks ought to be run (according to the docs) and shouldn't break anything if run each time it's more of a technicality.

# To do

- [ ] Make playbook support additional Operating Systems (e.g. CentOS)
- [x] Break out sub-tasks such as docker_install, ansible_install
- [ ] ~~Create 'Uninstall' role~~

## License
GPL-3.0-or-later
