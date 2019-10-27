create_mysql_dbs_and_users
=========

Ansible role to create one or more MySQL databases and users.

Requirements
------------

Must be using some compatible form of MySQL Server (MariaDB / MySQL / Percona)

Role Variables
--------------

(Required) Root password for MySQL Server

```
    create_mysql_dbs_and_users_mysql_root_password: "Some secure root password"
```
Database to setup. Required unless "create_mysql_dbs_and_users_use_list" is set to true.

```
    create_mysql_dbs_and_users_db_name: "database-to-setup"
```
Database user to setup. Required unless "create_mysql_dbs_and_users_use_list" is set to true.

```
    create_mysql_dbs_and_users_db_user: "user-to-setup"
```
Password database user.  Required unless "create_mysql_dbs_and_users_use_list" is set to true.

```
    create_mysql_dbs_and_users_db_password: "password-for-new-user"
```
List of databases and users to setup. Not needed unless the "create_mysql_dbs_and_users_use_list" variable is set to true. Default is false.

```
    create_mysql_dbs_and_users_list_to_setup:
      - {
          name: 'my-db-to-create',
          create_db: true,
          create_user: true,
          mysql_user: 'some-user',
          mysql_password: 'some-password',
          mysql_user_privileges: '*:ALL'
        }
```
(Default) Will you be passing a list of databases and/or database users to setup?

```
    create_mysql_dbs_and_users_use_list: false
```
(Default) Should we create the databases, or skip the DB creation and just create the users?

```
    create_mysql_dbs_and_users_create_db: true
```
(Default) Should we create the user, or skip the user creation and just create the database(s)?

```
    create_mysql_dbs_and_users_create_user: true
```
(Default) Privileges to grant DB user that is created

```
    create_mysql_dbs_and_users_privileges: '*:TRIGGER,CREATE ROUTINE,CREATE TEMPORARY TABLES,CREATE VIEW,ALTER ROUTINE,REFERENCES,EVENT,SHOW VIEW,EXECUTE,ALTER,DROP,CREATE,INDEX,SELECT,INSERT,UPDATE,DELETE'
```

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
	- hosts: your_server
	  vars_files:
	    - vars/main.yml
	  roles:
	    - stancel.create_mysql_dbs_and_users 
```

or just pass the variables in the playbook

```
	- hosts: your_server 
	  vars:
		create_mysql_dbs_and_users_mysql_root_password: "my-secure-password"
		create_mysql_dbs_and_users_db_name: "my-awesome-db"
		create_mysql_dbs_and_users_db_user: "my-db-user"
		create_mysql_dbs_and_users_db_password: "my-db-users-password"
	  roles:
	    - stancel.create_mysql_dbs_and_users
```

License
-------

GPLv3

Author Information
------------------

[Brad Stancel](https://github.com/stancel)
