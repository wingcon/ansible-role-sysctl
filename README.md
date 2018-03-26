# role_name

Configuration of sysctl system configuration.
Uses and changes the sysctl.conf file.

## Requirements

- Ansile >= 2.4

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml` and `vars/main.yml`.

## Dependencies

None.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

  - name: test sysctl role
    hosts: all
    roles:
      - role: amtega.sysctl
        vars:
          sysctl_options_list:
        #  [service]:
        #    option_name:
        #    option_value:
        #    option_status: [present | absent]
            rp_filter:
              option_name: net.ipv4.conf.all.rp_filter
              option_value: 1
              option_status: "absent"

            accept_source_route:
              option_name: "net.ipv4.conf.all.accept_source_route"
              option_value: 0
              option_status: "absent"

            all_accept_redirects:
              option_name: net.ipv4.conf.all.accept_redirects
              option_value: 0ansible-playbook --skip-tags "role::docker_engine" main.yml
              option_status: "present"

            default_accept_redirects:
              option_name: net.ipv4.conf.default.accept_redirects
              option_value: 0
              option_status: "present"


## Testing

Test are based on docker containers. You can run the tests with the following commands:

```shell
$ cd amtega.sysctl/tests
$ ansible-playbook main.yml
```

If you have docker engine configured you can avoid running dependant 'docker_engine' role (that usually requries root privileges) with the following commands:

```shell
$ cd amtega.sysctl/tests
$ ansible-playbook --skip-tags "role::docker_engine" main.yml

If you dont use docker containers:

```shell
$ cd amtega.sysctl/tests
$ ansible-playbook -u [ssh_user] -kK main-hosts.yml


## License

Copyright (C) <YEAR> AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify
it under the terms of:
GNU General Public License version 3, or (at your option) any later version;
or the European Union Public License, either Version 1.2 or – as soon
they will be approved by the European Commission ­subsequent versions of
the EUPL;

This role is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details or European Union Public License for more details.

## Author Information

- author_name Carlos Chedas Fernandez
