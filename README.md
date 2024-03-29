# Ansible role : OhMyZsh

[![Ansible Role](https://img.shields.io/ansible/role/d/pandemonium1986/init?logo=Ansible&color=blue)](https://galaxy.ansible.com/ui/standalone/roles/pandemonium1986/ohmyzsh/)
[![Molecule](https://github.com/Pandemonium1986/ansible-role-init/actions/workflows/molecule.yml/badge.svg)](https://github.com/Pandemonium1986/ansible-role-ohmyzsh/actions/workflows/molecule.yml)
![GitHub release](https://img.shields.io/github/release/Pandemonium1986/ansible-role-ohmyzsh.svg?logo=github)
![Github license](https://img.shields.io/github/license/Pandemonium1986/ansible-role-ohmyzsh.svg?logo=github)

Install and configure oh-my-zsh for any user.

## Requirements

This role is self contained. He installs zsh and git packages for debian, ubuntu, opensuse, sles, centos if needed.

## Role Variables

From defaults/main.yml :

```yaml
ohmyzsh_users:
  - user_name: pandemonium
    user_group: pandemonium
    user_home: /home/pandemonium/

ohmyzsh_config:
  - { regexp: '^ZSH_THEME="robbyrussell"$', line: 'ZSH_THEME="agnoster"' }
  - { regexp: '^# ENABLE_CORRECTION="true"$', line: 'ENABLE_CORRECTION="true"' }
  - { regexp: '^plugins=\(.*\)', line: "plugins=({{ ohmyzsh_plugins }})" }

ohmyzsh_plugins: >-
  ansible
  colored-man-pages
  composer
  debian
  docker
  docker-compose
  extract
  git
  git-flow
  history
  kubectl
  minikube
  ssh-agent
  vagrant
  zsh-autosuggestions
  zsh-syntax-highlighting

```

From vars/[distro|familly]-[os_familly]-[os_version].yml (depends of distribution):

```yaml
_packages:
  - git
  - sudo
  - zsh
```

## Dependencies

None.

## Example Playbook

```yaml
- name: OhMyZsh play
  hosts: pandama
  become: true
  become_method: sudo
  become_user: root
  tasks:
    - import_role:
        name: pandemonium1986.ohmyzsh
```

Warning : dont forget to set pipelining : True in your ansible.cfg for bypass file [Becoming an Unprivileged User](https://docs.ansible.com/ansible/latest/user_guide/become.html)

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details

## Author Information

- **Jérémy Baumgarth** - _Initial work_ - [jebovic](https://github.com/jebovic)
- **Michael Maffait** - _Customize_ - [Pandemonium1986](https://github.com/Pandemonium1986)
