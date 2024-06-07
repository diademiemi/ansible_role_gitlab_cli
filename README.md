Ansible Role GitLab CLI
=========

[![Molecule Test](https://gitlab.com/diademiemi/ansible_role_gitlab_cli/actions/workflows/molecule.yml/badge.svg)](https://gitlab.com/diademiemi/ansible_role_gitlab_cli/actions/workflows/molecule.yml)

This is an Ansible role to install gitlab_cli.

Requirements
------------
These platforms are supported:
- Ubuntu 20.04
- Ubuntu 22.04
- Debian 11
- Debian 12
- EL 8 (Tested on Rocky Linux 8)
- EL 9 (Tested on Rocky Linux 9)
- Fedora 40
- openSUSE Leap 15.5

<!--
- List hardware requirements here  
-->

Role Variables
--------------

Variable | Default | Description
--- | --- | ---
gitlab_cli_package_version | `"1.29.0"` | Version of GitLab CLI to install
gitlab_cli_package_url | [See [vars/main.yml](./vars/main.yml)] | URL of GitLab CLI package
gitlab_cli_package_path | `"/tmp/"` | Temporary path to download GitLab CLI package

<!--
`variable` | `default` | Variable example
`long_variable` | See [defaults/main.yml](./defaults/main.yml) | Variable referring to defaults
`distro_specific_variable` | See [vars/debian.yml](./vars/debian.yml) | Variable referring to distro-specific variables
-->

Dependencies
------------
<!-- List dependencies on other roles or criteria -->
None

Example Playbook
----------------

```yaml
- name: Use diademiemi.gitlab_cli role
  hosts: "{{ target | default('gitlab_cli') }}"
  roles:
    - role: "diademiemi.gitlab_cli"
      tags: ['diademiemi', 'gitlab_cli', 'setup']

```

License
-------

MIT

Author Information
------------------

- diademiemi (@diademiemi)

Role Testing
------------

This repository comes with Molecule that run in Podman on the supported platforms.
Install Molecule by running

```bash
pip3 install -r requirements.txt
```

Run the tests with

```bash
molecule test
```

These tests are automatically ran by Gitlab Actions on push. If the tests are successful, the role is automatically published to Ansible Galaxy.

Gitlab Actions is supposed to fail for this gitlab_cli repository, as it does not contain any meaningful role. There is an explicit assertion to check if the role name has been changed from `gitlab_cli` which causes the test to fail.  
