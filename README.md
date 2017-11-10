ansible-role-postgres
=========
[![travis](https://travis-ci.org/pyslackers/ansible-role-postgres.svg?branch=master)](https://travis-ci.org/pyslackers/ansible-role-postgres)

Ansible role to install and create postgresql databases.

Role Variables
--------------

* `postgres_version`: Version of postgres (default to `10`).
* `postgres_locale`: Locale used for postgres databases (default to `en_US.UTF-8`).
* `postgres_default_roles`: List of default user roles (default to `NOSUPERUSER,NOCREATEDB,NOCREATEROLE`).

* `postgres_users`: Dict of users and databases to creates with username as key.
    * `password`: User password.
    * `roles`: User roles (use `postgres_default_roles` if not set).
    * `database`: Name of database to create (default to the user name).

Example Playbook
----------------

```yml
- hosts: localhost
  vars:
    postgres_extra_packages:
      - pgtop
    postgres_users:
      test:
        password: PaSSw0rd
  roles: 
    - pyslackers.postgres
```

License
-------

MIT
