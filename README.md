# Ansible sysctl role

This is an [Ansible](http://www.ansible.com) role which manages sysctl configs.

## Requirements

[Ansible 2.7+](http://docs.ansible.com/ansible/latest/intro_installation.html)

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Dependencies

- [amtega.check_platform](https://galaxy.ansible.com/amtega/check_platform)
- [amtega.select_hostvars](https://galaxy.ansible.com/amtega/select_hostvars)

## Example Playbook

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - amtega.sysctl
  vars:    
    sysctl:
      - name: main        
        options:
          - name: kernel.printk
            value: 3 4 1 7#
          - name: net.ipv6.conf.all.disable_ipv6
            value: 1
      - name: hardlinks
        path: /etc/sysctl.d/50-hardlinks.conf
        options:
          - name: fs.protected_hardlinks
            value: 1
            state: present       
```

## Testing

Tests are based on docker containers. You can setup docker engine quickly using the playbook `files/setup.yml` available in the role [amtega.docker_engine](https://galaxy.ansible.com/amtega/docker_engine).

Once you have docker, you can run the tests with the following commands:

```shell
$ cd amtega.sysctl/tests
$ ansible-playbook main.yml
```

## License

Copyright (C) 2018 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- Carlos Chedas Fernández.
- Juan Antonio Valiño García.
