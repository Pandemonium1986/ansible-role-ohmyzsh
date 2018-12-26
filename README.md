# Ansible role : OhMyZsh

Install and configure oh-my-zsh for any user.

## Requirements

This roles is self contained and install Zsh from debian backports if needed.

## Role Variables

From defaults/main.yml :

```yaml
ohmyzsh_users:
  - user_name: root
    user_group: root
    user_home: /root
  - user_name: pandemonium
    user_group: pandemonium
    user_home: /home/pandemonium
  - user_name: vagrant
    user_group: vagrant
    user_home: /home/vagrant

ohmyzsh_plugins: git git-flow colored-man-pages composer chucknorris debian extract history kubectl minikube ssh-agent zsh-autosuggestions zsh-syntax-highlighting
```

From vars/main.yml :

```yaml
apt_packages:
  - zsh
  - git
  - curl
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: servers
  roles:
    - { role: pandemonium1986.ohmyzsh }
```

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details

## Author Information

* **Jérémy Baumgarth** - *Initial work* - [jebovic](https://github.com/jebovic)
* **Michael Maffait** - *Customize* - [Pandemonium1986](https://github.com/Pandemonium1986)
