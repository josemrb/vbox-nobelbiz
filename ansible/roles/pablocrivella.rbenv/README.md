# Ansible Role: Rbenv

[![Build
 Status](http://img.shields.io/travis/pablocrivella/ansible-role-rbenv.svg?style=flat)](http://travis-ci.org/pablocrivella/ansible-role-rbenv)
[![Ansible
Galaxy](http://img.shields.io/badge/galaxy-pablocrivella.rbenv-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/2332)

Role to install rbenv and multiple ruby versions.

## Requirements

Tested with Ansible 1.8.4.

## Role Variables

```yaml
---
# This could be set to 'user' to support user installs.
rbenv_env: system

rbenv_version: v0.4.0

# This sets the rbenv global ruby version.
rbenv_global: 2.2.3

# List of ruby versions to install.
rbenv_rubies:
  - 2.2.3

# List of defaults gem to install on each ruby version.
rbenv_default_gems:
  - bundler

# List of users to install rbenv and ruby versions to.
# Ignored if rbenv_env is set to 'system'
rbenv_users: []

# Example:
# rbenv_users: []
#   - user1
#   - user2
```

## Dependencies

- ANXS.git
- ANXS.build-essential

## Example Playbook

```yaml
- hosts: ruby-devbox
  roles:
    - pablocrivella.rbenv
```

For a more detailed example check this [Playbook](https://github.com/pablocrivella/apps-forge/blob/master/provisioning/ruby.yml).

## License

MIT

## Author Information

Pablo Crivella Backend Engineer @ NobelBiz.
