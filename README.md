# URXVT

[![CICD](https://github.com/jahrik/ansible-urxvt/actions/workflows/cicd.yml/badge.svg)](https://github.com/jahrik/ansible-urxvt/actions/workflows/cicd.yml)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-jahrik.urxvt-blue?logo=ansible)](https://galaxy.ansible.com/ui/standalone/roles/jahrik/urxvt/)

Installs [rxvt-unicode](http://software.schmorp.de/pkg/rxvt-unicode.html) (urxvt) — a lightweight X11 terminal emulator — with font-size, keyboard-select, and url-select plugins. Deploys Xresources color schemes (dark/light) to `~/.urxvt/`. Depends on [jahrik.nerd_fonts](https://galaxy.ansible.com/ui/standalone/roles/jahrik/nerd_fonts/) for icon font support.

## OS Support

| Platform | Install method |
|---|---|
| Arch Linux | `pacman` (rxvt-unicode, urxvt-perls, ttf-dejavu, xsel) |
| Debian / Ubuntu | `apt` (rxvt-unicode, fonts-dejavu, xsel) |

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `install` | `true` | Set to `false` to uninstall urxvt |
| `browser` | `chromium` | Default browser (referenced in config templates) |
| `text.font` | `DejaVuSansMono Nerd Font` | Font family |
| `text.size` | `18` | Font size |

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - role: jahrik.urxvt
```

To uninstall:

```yaml
---
- hosts: all
  vars:
    install: false
  roles:
    - role: jahrik.urxvt
```

## Testing

```bash
uv sync
source .venv/bin/activate
yamllint .
ansible-lint
molecule test
```

## License

GPLv2

## Author Information

jahrik@gmail.com
