pyslackers.postgres
===================

[![Build Status](https://travis-ci.org/pyslackers/ansible-role-postgres.svg?branch=master)](https://travis-ci.org/pyslackers/ansible-role-postgres)

Ansible role to install and configure [PostgreSQL](https://www.postgresql.org/).

Installation
------------

To install this roles clone it into your roles directory.

```bash
$ git clone https://github.com/pyslackers/ansible-role-postgres.git pyslackers.postgres
```

If your playbook already reside inside a git repository you can clone it by using git submodules.

```bash
$ git submodule add -b master https://github.com/pyslackers/ansible-role-postgres.git pyslackers.postgres
```

Role Variables
--------------

* `postgres_version`: Version of postgres (default to `10`).
* `postgres_locale`: Locale used for postgres databases (default to `en_US.UTF-8`).
* `postgres_default_roles`: List of default user roles (default to `NOSUPERUSER,NOCREATEDB,NOCREATEROLE`).

* `postgres_listen_address`: Listening address of Postgres (default to `localhost`).
* `postgres_listen_port`: Listening port of Postgres (default to `5432`).

* `postgres_users`: Dict of users and databases to creates with username as key.
    * `password`: User password.
    * `roles`: User roles (use `postgres_default_roles` if not set).
    * `database`: Name of database to create (default to the user name).

* `postgres_clients`: List of clients allowed to connect.
    * `db`: Required.
    * `user`: Required.
    * `address`: Default to `127.0.0.1/32`.
    * `peer`: Default to `md5`.
    * `type`: Default to `host`.

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
