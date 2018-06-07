# Camac Role

Role for installing and configuring camac. This role takes care of unpacking a
camac release tarball on the installation target system.

I was written for deploying camac at the canton of Berne but might also prove
useful in other situations.

## Requirements

This role does not have any external dependencies needed to run it. Using a
fairly modern of Ansible is recommended.

## Role Variables

### Deployment settings

| variable | required | default | comments |
| -------- | -------- | ------- | -------- |
| `camac_customer_variables` | no | null | Path to a yaml file defining additional variables that override role variables |

### Version settings

| variable | required | default | comments |
| -------- | -------- | ------- | -------- |
| `camac_version` | yes | | Full version of Camac Release to install |
| `camac_tarball_checksum` | yes | | SHA256 checksum of Camac |
| `camac_release` | yes | | URL to Camac download |

### Directory settings

| variable | required | default | comments |
| -------- | -------- | ------- | -------- |
| `camac_basedir` | no | "/usr/share/camac" | This dir is used as the base for other paths. |
| `camac_docroot` | no | "{{ camac_basedir}}/htdocs" | This dir contains the appication entry point. |
| `camac_datadir` | no | "/var/lib/camac" | Storage directory for uploads to camac and other data. |
| `camac_releasedir` | no | "/tmp" | Directory to place the unpacked staging directory "camac" into. |
| `camac_logdir` | no | "{{ camac_basedir }}/log" | This dir contains application logs. |

### Camac Environment

| variable | required | default| comments |
| -------- | -------- | ------- | -------- |
| `camac_env` | no | "development" | Environment for Camac (may be "development", "testing" or, "production" |
| `camac_master` | no | True | Define if the current server is a master in the camac master/slave concept |

### Camac Configuration

| variable | required | default| comments |
| -------- | -------- | ------- | -------- |
| `camac_django_secret` | yes | | Secret string for django parts, must be set for each environment. |
| `camac_password_salt` | yes | | Passwort Salt String for Passwords managed by Zend Framework 1 |
| `camac_session_secure` | yes | 'false' | Set this to true to set the secure flag on camac cookies. |
| `camac_ca_chain` | no | | If set this value is used to create a PEM file that is configured as `openssl.cafile` in PHP |
| `camac_apache_user` | no | www-data | Set this to the Apache user on the target system. |
| `camac_base_domain` | no | camac.ch | This specifies the domain part of emails sent by camac. |

### Keycloak Configuration

| variable | required | default| comments |
| -------- | -------- | ------- | -------- |
| `camac_keycloak_enable` | yes | yes | Enable keycloak install and configuration, set to false to disable both. |
| `camac_keycloak_java_home` | no | null | Uses the java on $PATH if not specified. |
| `camac_auth_idp_url` | yes | `http://keycloak.127.0.0.1.nip.io:8080/auth` | External URL of IdP, camac needs to be abel to reach this IdP through this URL but it must also match the URL being used by the end-user. |
| `camac_auth_idp_realm` | yes | `ebau` | |
| `camac_auth_sp_client` | yes | camac | |

Dependencies
------------

This role expects most of the system to already be provisioned using other roles
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

This role is part of the [Camac project](http://camac.ch). It was created and
is maintained by [Adfinis SyGroup AG](https://adfinis-sygroup.ch/).
