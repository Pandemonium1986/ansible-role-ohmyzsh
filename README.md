# Ansible role : OhMyZsh

![](https://img.shields.io/github/release/Pandemonium1986/ansible-role-ohmyzsh.svg)
![](https://img.shields.io/github/repo-size/Pandemonium1986/ansible-role-ohmyzsh.svg)
![](https://img.shields.io/github/release-date/Pandemonium1986/ansible-role-ohmyzsh.svg)
![](https://img.shields.io/github/license/Pandemonium1986/ansible-role-ohmyzsh.svg)

Install and configure oh-my-zsh for any user.

## Requirements

This role is self contained. He installs zsh and git packages for debian, ubuntu, linux mint, centos if needed.

## Role Variables

From defaults/main.yml :

```yaml
ohmyzsh_users:
  - user_name:    pandemonium
    user_group:   pandemonium
    user_home:    /home/pandemonium/

ohmyzsh_config:
  - { regexp: '^ZSH_THEME="robbyrussell"$', line: 'ZSH_THEME="agnoster"'}
  - { regexp: '^# ENABLE_CORRECTION="true"$', line: 'ENABLE_CORRECTION="true"'}
  - { regexp: '^plugins=\(.*\)', line: 'plugins=({{ ohmyzsh_plugins }})'}

ohmyzsh_plugins:  >-
  ansible
  chucknorris
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

From vars/main.yml :

```yaml
_packages:
  - zsh
  - git
```

## Dependencies

None.

## Example Playbook

```yaml
- name :         OhMyZsh play
  hosts :        pandama
  become:        true
  become_method: sudo
  become_user:   root
  tasks:
    - import_role:
        name:    pandemonium1986.ohmyzsh
```

Warning : dont forget to set pipelining : True in your ansible.cfg for bypass file [Becoming an Unprivileged User](https://docs.ansible.com/ansible/latest/user_guide/become.html)

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details

## Author Information

-   **Jérémy Baumgarth** - _Initial work_ - [jebovic](https://github.com/jebovic)
-   **Michael Maffait** - _Customize_ - [Pandemonium1986](https://github.com/Pandemonium1986)
