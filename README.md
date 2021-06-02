# Ansible GitLab Runner

[![CI](https://github.com/akutschi/ansible_gitlab_runner/actions/workflows/ci.yml/badge.svg)](https://github.com/akutschi/ansible_gitlab_runner/actions/workflows/ci.yml)

This is a very simple role to install the GitLab Runner and the Docker components.

## Requirements

This role does not have any requirements.

## Coverage

Any combination of the following is tested:

- Operating System
  - Ubuntu 20.04 LTS
  - Debian 10
- Ansible
  - 2.9.x
  - 3.x
  - 4.x 
- Python
  - 3.8
  - 3.9

## Install Role

To install this role into your `roles` folder just clone, download or run: 

```bash
ansible-galaxy install --roles-path ./roles git+https://github.com/akutschi/ansible_gitlab_runner.git,v0.2.0
```

## Role Variables

There are no settable variables in this role.

## Dependencies

This role does not have any dependencies.

## Example Playbook

```yml
---
- hosts: servers
  roles:
      - ansible_gitlab_runner
```

## Register Runner

This role does not register the runner. This has to be done manually:

```sh
gitlab-runner register \
--non-interactive \
--url "https://gitlab.com/" \
--registration-token "TOKEN" \
--executor "docker" \
--docker-image alpine:latest \
--tag-list $(uname -m),$(uname -o),docker \
--run-untagged="true" \
--name "$HOSTNAME"
```

The token for group and repo runners can be found under `Settings -> CI/CD -> Runners`. 

The reason for this manual step is, that one machine can have several runner configurations. 
And on top of that, if there will be several machines deployed for different architectures things get quickly difficult.

# License

GPLv3, see [license](./LICENSE).

# Contributing

Feel free to open issues or merge requests if you find problems or have ideas for improvements. Thank you.