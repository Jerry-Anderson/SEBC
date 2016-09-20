# MySQL/MariaDB Installation Lab
## Configure MariaDB with a replica server

### Install MariaDB
	Master 1
	- sudo yum install mariadb-server
	
	Master 2
	- sudo yum install mariadb-server

### Configure MariaDB
	- MariaDB is already stopped
	- /var/lib/mysql/ib_logfile0 and /var/lib/mysql/ib_logfile1 do not exist
#### Master 1
	- Created /etc/my.cnf.d/cloudera_master.conf on Master 1
```
[mysqld]
transaction-isolation = READ-COMMITTED
# Disabling symbolic-links is recommended to prevent assorted security risks;
# to do so, uncomment this line:
# symbolic-links = 0

# Configure Replication
server_id=1
log-basename=master1
bind-address=172.31.29.173

key_buffer = 16M
key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1

max_connections = 550
#expire_logs_days = 10
#max_binlog_size = 100M

#log_bin should be on a disk with enough free space. Replace '/var/lib/mysql/mysql_binary_log' with an appropriate path for your system
#and chown the specified folder to the mysql user.
log_bin=/var/lib/mysql/mysql_binary_log

binlog_format = mixed

read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M

# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid
```
	- ran mysql_secure_installation
	- Grant replication priviledges
		- GRANT REPLICATION SLAVE ON *.* TO 'replication_user'@'ip-172-31-29-174' IDENTIFIED BY 'replication';
		- SET GLOBAL binlog_format = 'ROW';
		- FLUSH TABLES WITH READ LOCK; 
		- Open 2nd MySQL session
			- SHOW MASTER STATUS;
			- Record Log File and Position (empty)

#### Master 2
	- Created /etc/my.cnf.d/cloudera_slave.conf on Master 2
```
[mysqld]
transaction-isolation = READ-COMMITTED
# Disabling symbolic-links is recommended to prevent assorted security risks;
# to do so, uncomment this line:
# symbolic-links = 0

# Configure Replication
server_id=2
bind-address=172.31.29.174

key_buffer = 16M
key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1

max_connections = 550
#expire_logs_days = 10
#max_binlog_size = 100M

#log_bin should be on a disk with enough free space. Replace '/var/lib/mysql/mysql_binary_log' with an appropriate path for your system
#and chown the specified folder to the mysql user.
#log_bin=/var/lib/mysql/mysql_binary_log

#binlog_format = mixed

read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M

# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid
```
	- Connect Slave to the Master
	- CHANGE MASTER TO MASTER_HOST='ip-172-31-29-173', MASTER_USER='replication_user', MASTER_PASSWORD='replication';
	- 