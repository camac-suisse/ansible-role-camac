# Camac Role

Role for installing and configuring camac. This role takes care of unpacking a
camac release tarball on the installation target system.

I was written for deploying camac at the canton of Berne but might also prove
useful in other situations.

## Requirements

This role does not have any external dependencies needed to run it. Using a
fairly modern of Ansible is recommended.

## Role Variables

### Version settings

| variable | required | default | comments |
| -------- | -------- | ------- | -------- |
| `camac_version` | yes | | Full version of Camac Release to install |
| `camac_tarball_checksum` | yes | | Checksum of Camac |
| `camac_release` | yes | | URL to Camac download |

### Directory settings

| variable | required | default | comments |
| -------- | -------- | ------- | -------- |
| `camac_basedir` | no | "/usr/share/camac" | This dir is used as the base for other paths. |
| `camac_docroot` | no | "{{ camac_basedir}}/htdocs" | This dir contains the appication entry point. |
| `camac_datadir` | no | "/var/lib/camac" | Storage directory for uploads to camac and other data. |

Dependencies
------------

This rol expects most of the system to already be provisioned using other roles
that are customer specific (ie. there is already a pre-existing apache2 role at
the customers site).

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: camac }

License
-------

As is

Author Information
------------------

This role is part of the Camac project. It was created and is maintained 
by [Adfinis SyGroup AG](https://adfinis-sygroup.ch/).
