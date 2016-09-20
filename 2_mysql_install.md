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
	- ran mysql_secure_installation
	- Created /etc/my.cnf.d/cloudera_master.cnf on Master 1
```
[mysqld]
transaction-isolation = READ-COMMITTED
# Disabling symbolic-links is recommended to prevent assorted security risks;
# to do so, uncomment this line:
# symbolic-links = 0

#skip-networking
#bind-address=172.31.29.173

# Configure Replication
server_id=1
log-basename=master1
log-bin
binlog-format=row
```
	- Grant replication priviledges
		- GRANT REPLICATION SLAVE ON *.* TO 'replication_user'@'ip-172-31-29-174.ec2.internal' IDENTIFIED BY 'replication';
		- FLUSH TABLES WITH READ LOCK; 
###### Open 2nd MySQL session
```
SHOW MASTER STATUS;

			+--------------------+----------+--------------+------------------+
| File               | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+--------------------+----------+--------------+------------------+
| mariadb-bin.000001 |      245 |              |                  |
+--------------------+----------+--------------+------------------+
```
			- Record Log File and Position

#### Master 2
	- Created /etc/my.cnf.d/cloudera_slave.cnf
```
[mysqld]
transaction-isolation = READ-COMMITTED
# Disabling symbolic-links is recommended to prevent assorted security risks;
# # to do so, uncomment this line:
# # symbolic-links = 0

#skip-networking
#bind-address = 172.31.29.174

# Configure Replication
server_id = 2
```
###### Connect Slave to the Master
	- CHANGE MASTER TO MASTER_HOST='ip-172-31-29-173.ec2.internal', MASTER_USER='replication_user', MASTER_PASSWORD='replication', MASTER_LOG_FILE='mariadb-bin.000001', MASTER_LOG_POS=245;

###### Download MariaDB JDBC Connector
All nodes
```
http://dev.mysql.com/downloads/connector/j/5.1.html
```
```
tar -xzvf mysql-connector-java-5.1.39.tar.gz
```
```
sudo mkdir -p /usr/share/java/
```
```
sudo cp mysql-connector-java-5.1.39/mysql-connector-java-5.1.39-bin.jar /usr/share/java/mysql-connector-java.jar
```
###### Create External Databases
```
mysql -u root -p < create_dbs.sql
```
```
/*
 * Script to create Cloudera External DBs
 *
 */
create database rman DEFAULT CHARACTER SET utf8;
grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman';
create database metastore DEFAULT CHARACTER SET utf8;
grant all on metastore.* TO 'hive'@'%' IDENTIFIED BY 'hive';
create database sentry DEFAULT CHARACTER SET utf8;
grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'sentry';
create database nav DEFAULT CHARACTER SET utf8;
grant all on nav.* TO 'nav'@'%' IDENTIFIED BY 'nav';
create database navms DEFAULT CHARACTER SET utf8;
grant all on navms.* TO 'navms'@'%' IDENTIFIED BY 'navms';
```
###### Configure HUE DB
```
Add the following to /etc/my.cnf.d/cloudera_master.cnf

sql_mode=STRICT_ALL_TABLES
```
```
Restart MariaDB

sudo systemctl restart mariadb.service
```
```
Create hue database and give permission

mysql -u root -p -e 'CREATE DATABASE hue';
mysql -u root -p -e "grant all on hue.* to 'hue'@'localhost' identified by 'hue';"
mysql -u root -p -e "grant all on hue.* to 'hue'@'%' identified by 'hue';"
```
###### Configure Oozie DB
```
Create Oozie database and give permission

mysql -u root -p -e 'CREATE DATABASE oozie';
mysql -u root -p -e "grant all on oozie.* to 'oozie'@'localhost' identified by 'oozie';"
mysql -u root -p -e "grant all on oozie.* to 'oozie'@'%' identified by 'oozie';"
```
###### Download Cloudera repo to all nodes
```
wget -O /etc/yum.repos.d/cloudera_rhel7.repo https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo?_ga=1.133468105.674561133.1471284970
```
###### Install Oracle JDK
```
sudo yum -y install oracle-j2sdk1.7
```
### Preparing Cloudera Manager External DB
###### Install Cloudera Manager Packages
```
sudo yum install cloudera-manager-daemons cloudera-manager-server
```
###### Run prepare script
```
sudo /usr/share/cmf/schema/scm_prepare_database.sh -u root -ppassword mysql scm scm scm
```
### Start Cloudera Manager
```
sudo systemctl start cloudera-scm-server.service
```
### Access Cloudera Manager 
###### In a browser
```
http://ec2-75-101-204-230.compute-1.amazonaws.com:7180/cmf/login
```
###### Login
```
admin:admin
```
###### Follow the Wizard to create cluster
	- Accept Terms
	- Data Hub Trial License
	- Continue
	- Enter all host names
		- 172.31.29.173
		- 172.31.29.174
		- 172.31.29.175
		- 172.31.29.176
		- 172.31.29.177
	- Verify all hosts found, continue
	- Accept defaults for Select Repository
	- Install JDK and Encryption policy files
	- DO NOT enable single user
	- Install page
		- Select another user, centos
		- provide private key
		- no passphrase
		- use remaining defaults
	- Wait for Install to complete, continue
	- Wait for Download, Distribute, Unpack and Activate, continue
	- View Host Inspector Output and resolve issues
	- Finish

###### MySQL JDBC for Oozie 
```
Distribute MySQL JDBC for Oozie (Master 2)

sudo cp mysql-connector-java-5.1.39/mysql-connector-java-5.1.39-bin.jar /var/lib/oozie/mysql-connector-java.jar
``` 
###### Cluster Setup 
	- Select 'Core Hadoop'
	- Role Assignments
		- Spread Services across two master nodes
	- Database Setup
		- Enter details from database creation
		- Update DB location for services on Master 2
	- Test Connection, continue upon successful connection
	- Review Changes
		- Accept defaults
	- Wait for 'First Run', continue
	- Completed

## Review Cluster Dashboard
	- Fix Configuration messages
	- Restart Service and Re-Deploy configurations

## Bonus Lab
###### Install HTTP
```
sudo yum install httpd
```
###### Start HTTP
```
sudo systemctl start httpd.service
```

	    