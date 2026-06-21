# AGENTS.md

This file provides guidance to AI coding agents when working with code in this repository.

## Role Overview

Installs and configures [rxvt-unicode (urxvt)](http://software.schmorp.de/pkg/rxvt-unicode.html), a lightweight terminal emulator. Deploys Xresources color schemes (dark/light) to `~/.urxvt/` and installs the font-size and keyboard-select/url-select plugins.

## Key Variables

| Variable | Default | Description |
|---|---|---|
| `install` | `true` | Set to `false` to skip install |
| `browser` | `chromium` | Default browser (referenced in config templates) |
| `text.font` | `DejaVuSansMono Nerd Font` | Font family |
| `text.size` | `18` | Font size |

## Task Flow

- `tasks/main.yml` — includes OS-specific tasks, creates `~/.urxvt/ext/`, templates config files, downloads font-size plugin, symlinks keyboard-select/url-select (Arch only)
- `tasks/archlinux.yml` — installs via `community.general.pacman`
- `tasks/debian.yml` — updates apt cache, installs via `apt`

## Testing

```bash
yamllint .
ansible-lint
molecule test
molecule converge
molecule destroy
```

## CI

- **Lint**: yamllint + ansible-lint
- **Molecule**: Ubuntu 24.04 + Arch Linux via Docker
- **Release**: publishes to Ansible Galaxy on merge to `main`
