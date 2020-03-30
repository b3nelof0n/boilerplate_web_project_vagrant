# Ansible Role: mysql

Ansible role which installs and configures MySQL. Well, not really. We're
actually installing Percona. But don't tell anyone.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    mysql_flavour: "percona"

The MySQL flavour to install. Can be either one of "mariadb" or "percona".
Vanilla MySQL is currently not supported, but should be trivial to add.

    mysql_version: "5.6"

The MySQL version to install.

    mysql_root_password: my_password
    mysql_root_password_encrypted: no

The MySQL root password, and whether it is encrypted or not.

    mysql_databases:
      - example

The MySQL databases to create.

    mysql_users:
      myuser:
        username: myuser
        password: mypassword
        password_encrypted: yes/no (default = no)
        priv: "example.*:ALL"
        host: "%"

The MySQL users and their permissions.

    mysql_bind_address: 0.0.0.0

The IP address to bind the MySQL server to.

    mysql_server_id: 100

The MySQL server ID, useful in master-slave scenarios. Not set by default.

    mysql_log_bin: /var/log/mysql/mysql-bin.log

If and where to store the MySQL binary lofs. Not set by default.


Various performance settings:
    mysql_user_connections: 400
    mysql_max_connections: 500
    mysql_innodb_thread_concurrency: 16
    mysql_innodb_buffer_pool_size: 2048M
    mysql_innodb_flush_log_at_trx_commit: 1
    mysql_innodb_write_io_threads: 4
    mysql_innodb_read_io_threads: 4
    mysql_innodb_buffer_pool_instances: 8
    mysql_innodb_log_file_size: 4M

Other settings:
    mysql_sql_mode
    mysql_expire_logs_days
    mysql_max_binlog_size

## Example Playbook

    - hosts: servers
      roles:
         - { role: tigron.mysql }

## License

MIT

## Author Information

Created by Gerry Demaret for [Tigron bvba](http://tigron.be/).
