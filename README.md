# jonsible.builder

[![Build Status](https://travis-ci.com/jonsible/builder.svg?branch=master)](https://travis-ci.com/jonsible/builder)
[![Galaxy](https://img.shields.io/badge/galaxy-jonsible.builder-blue.svg)](https://galaxy.ansible.com/jonsible/builder/)

Role to install builder

## Requirements

None.

## Role Variables

### Default usage

As default builder is installed and running.
If you want to adapt this to your needs look at the [Advanced usage](#advanced-usage) section.

### Advanced usage

You will have to specify build specs like this
```yaml
_name: tmux
version: 2.9
owner: root
prefix: /usr/local

dependencies:
  Archlinux:
    - base-devel
  Debian-family:
    - build-essential
  RedHat-family:
    - "@Development Tools"

# Clone and Fetch mutually exclusive
clone:
  repo: https://github.com/tmux/tmux.git

fetch:
  url: https://github.com/tmux/tmux/releases/download/2.9/tmux-2.9.tar.gz
  extra_opts:
    - --strip-components=1

prepare:
  shell: |
    ./bootstrap
    patch < apply.diff

build:
  shell: |
    ./configure \
    --prefix={{ prefix }} \
    --enable-ipv6 \
    make -j4

install:
  shell: |
    make install
  creates: "{{ prefix }}/bin/{{ _name }}"

uninstall:
  shell: |
    make uninstall
  removes: "{{ prefix }}/bin/{{ _name }}"
```

To specify dependencies for a specific distribution, create a key matching ansible_distribution in the `dependencies` dict.
```yaml
dependencies:
  Ubuntu:
    - build-essential
```
For an OS family, add -family to the ansible_os_family
```yaml
dependencies:
  Debian-family:
    - build-essential
```

## Dependencies

None

## Example Playbook

Install builder with the default settings
```yaml
- hosts: all
  roles:
     - role: jonsible.builder
```

## License

GPL-3.0-or-later

## Author Information

This role was created in 2020 by [Jonathan Scherrer].
