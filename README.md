# oh-my-zsh

This is an Ansible Role to install oh-my-zsh and configure your .zshrc file.
This is built around the default config file so if things are missing, let me know.

I made this so for when I needed to remote into a device and wanted to have the same config for all my nodes.

## Themes

To review the currently installed themes check [here](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes).
Take the name that you want to use and add it to either `zsh_theme` or `zsh_theme_random_candidates`.

## Plugins

[Installed Plugins](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins)
Take the name of the plugin that you want to use and add it to `zsh_plugins`.

## Platforms

Currently, this supports 

## Variables

``` yaml

# Defines where ohmyzsh will be installed.
# Example: /home/username
# Default: ''
zsh_ohmyzsh_install: string

# Defines the theme that will be enabled
# https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
# Example: robbyrussell
# Default: 'robbyrussell'
zsh_theme: string

# Defines what random theme will be picked if zsh_theme is 'random'
# Example: "'robbyrussell' 'agnoster'"
# Default: ''
zsh_theme_random_candidates: string

# Defines if zsh will use case-sensitive completion
# If left with Default value this line is commented out
# Example: true
# Default: false
zsh_case_sensitive: bool

# Default: false
zsh_hyphen_insensitive: bool

# Default: false
zsh_disable_auto_update: bool

# default: 13
zsh_update_days: int

# Default: false
zsh_disable_ls_colors: bool

# Default: false
zsh_disable_auto_title: bool

# Default: false
zsh_enable_correction: bool

# Default: false
zsh_completion_waiting_dots: bool

# Default: false
zsh_disable_untracked_files_dirty: bool

# Default: null
zsh_hist_stamps: string

# Default: 'git'
zsh_plugins: string

```

## Examples

``` yaml
- name: Install ohmyzsh and generate a file
  hosts: localhost
  vars:
    zsh_backup: false
    zsh_ohmyzsh_install: /home/luther38
    zsh_plugins: git ansible dotenv

  roles:
    - luther38.ohmyzsh
```

``` yaml
- name: Install ohmyzsh and pull a remote file
  hosts: localhost
  vars:
    zsh_backup: true
    zsh_ohmyzsh_install: /home/luther38
    zsh_download_url: 'https://raw.githubusercontent.com/geerlingguy/dotfiles/master/.zshrc'

  roles:
    - ansible-role-ohmyzsh
```

## Requirements.yml

This repo is not published in galaxy and might never be.  To use this role you will need to either clone or add these lines to your requirements.yml file.

``` yml
roles:
  - src: https://github.com/luther38/ansible-role-ohmyzsh
    name: luther38.ohmyzsh
    version: master
```
