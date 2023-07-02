# ansible-role-waypoint

[![molecule](https://github.com/diodonfrost/ansible-role-waypoint/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-waypoint/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.waypoint-660198.svg)](https://galaxy.ansible.com/diodonfrost/waypoint)

This role provide a compliance for install waypoint on your target host.

## Requirements

None.

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
# defaults file for ansible-role-waypoint

# Define waypoint version to install
# Possible values: https://releases.hashicorp.com/waypoint/index.json
# Default: latest
waypoint_version: latest

# Define where to install waypoint binary
# Default: use local system path defined in Ansible vars/*.yml
waypoint_path: "{{ waypoint_default_path }}"
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy waypoint role in a localhost and installing the latest version of waypoint.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.waypoint
```

This role can also install a specific version of waypoint.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: ansible-role-waypoint
      vars:
        waypoint_version: 0.11.2
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
* [Virtualbox](https://www.virtualbox.org/) (if you test windows system)
* [Vagrant](https://www.vagrantup.com/downloads.html) (if you test windows system)

### Testing with Docker

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 22.04
molecule test

# Test ansible role with ubuntu 20.04
image=ansible-ubuntu:20.04 molecule test

# Test ansible role with alpine latest
image=ansible-alpine:latest molecule test

# Create ubuntu 22.04 instance
molecule create

# Apply role on ubuntu 22.04 instance
molecule converge

# Launch tests on ubuntu 22.04 instance
molecule verify
```

### Testing with Vagrant and Virtualbox

```shell
# Test ansible role with FreeBSD
molecule test -s freebsd

# Test ansible role with OpenBSD
molecule test -s openbsd

# Test ansible role with Solaris
molecule test -s solaris

# Test ansible role with Windows
molecule test -s windows
```

## License

Apache 2

## Author Information

This role was created in 2023 by diodonfrost.