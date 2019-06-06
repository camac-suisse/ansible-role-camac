# Camac Role
Role for installing and configuring camac ecosystem. This role takes care of unpacking a
camac release tarball on the installation target system.

It was written for deploying camac at the canton of Berne but might also prove
useful in other situations.

## Requirements
This role does not have any external dependencies needed to run it. Using a
fairly modern of Ansible is recommended.

## Configuration
A detailed description on how this role can be configured, can be seen here
* [Defaults](defaults/main.yml)
* [Variables](vars/main.yml)


## Dependencies
This role expects most of the system to already be provisioned using other roles
that are customer specific (ie. there is already a pre-existing apache2 role at
the customers site).

## License
As is

## Author Information
This role is part of the [Camac project](http://camac.ch). It was created and
is maintained by [Adfinis SyGroup AG](https://adfinis-sygroup.ch/).
