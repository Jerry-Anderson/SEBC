# Integrating Kerberos with Cloudera Manager
## Install openldap-clients (CM)
```
sudo yum install openldap-clients
```
## Install MIT KDC (Master 2)
```
sudo yum install krb5-server openldap-clients krb5-workstation
```
## Install krb5-workstation, krb5-libs (All Hosts)
```
sudo yum install krb5-workstation krb5-libs
```
## Configure /etc/krb5.conf
```
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 dns_lookup_realm = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true
 renewable = true
 rdns = false
 default_realm = LOCAL
 default_ccache_name = KEYRING:persistent:%{uid}

[realms]
 LOCAL = {
  kdc = localhost
  admin_server = localhost
 }

[domain_realm]
 .local = LOCAL
 local = LOCAL
```
## Verify UnlimitedJCEPolicyJDK7
```
$ ls /usr/java/jdk1.7.0_67-cloudera/jre/lib/security/*.jar

local_policy.jar
US_export_policy.jar
```
## Create Kerberos Database
```
sudo kdb5_util create -s
```
## Verify /var/kerberos/krb5kdc/kadm5.acl
```
$ sudo cat /var/kerberos/krb5kdc/kadm5.acl

*/admin@LOCAL	   *
```
## Configure /var/kerberos/krb5kdc/kdc.conf
```
$ sudo cat /var/kerberos/krb5kdc/kdc.conf

[kdcdefaults]
 kdc_ports = 88
 kdc_tcp_ports = 88

[realms]
 LOCAL = {
  #master_key_type = aes256-cts
  acl_file = /var/kerberos/krb5kdc/kadm5.acl
  dict_file = /usr/share/dict/words
  maxrenewlife = 7d
  max_life = 1d
  admin_keytab = /var/kerberos/krb5kdc/kadm5.keytab
  supported_enctypes = aes256-cts:normal aes128-cts:normal des3-hmac-sha1:normal arcfour-hmac:normal camellia256-cts:normal camellia128-cts:normal des-hmac-sha1:normal des-cbc-md5:normal des-cbc-crc:normal
  default_principal_flags = +renewable,+forwardable
 }
```
## Start and Enable KDC
```
systemctl start  krb5kdc.service
systemctl enable krb5kdc.service
systemctl start  kadmin.service
systemctl enable kadmin.service
```
## Create Principals
```
sudo kadmin.local -q "addprinc -pw local root/admin@LOCAL"
sudo kadmin.local -q "addprinc -pw local cloudera-scm/admin@LOCAL"
sudo kadmin.local -q "addprinc -pw local hdfs@LOCAL"
```
## Create Linux User and Principal
```
sudo useradd jerry-anderson
sudo kadmin.local -q "addprinc -pw local jerry-anderson@LOCAL"
```
## Set minimum user id
In CM, Yarn -> Configuration -> Search "user.id"

Set = 100, save changes

## Enable Kerberos Wizard
cluster name (jerry-anderson) drop-down -> "Enable Kerberos"
### Screen 1 of 9
Verify Prerequisites
### Screen 2 of 9
#### KDC Type
```
MIT KDC
```
#### KDC Server Host
```
ip-172-31-29-174.ec2.internal
```
#### KDC Security Realm
```
LOCAL
```
#### KDC Encryption Types
```
aes256-cts-hmac-sha1-96
```
#### Maximum Renewable Life for Principals
```
7 days
```
### Screen 3 of 9
#### KRB5 Configuration
##### Manage krb5.conf through Cloudera Manager
```
Check Box

Accept remaining defaults
```
### Screen 4 of 9
#### KDC Account Manager Credentials
```
Username:  cloudera-scm/admin@LOCAL
Password:  local
```
### Screen 5 of 9
#### Import KDC Account Manager Credentials
```
Status: Finished Start Time: Sep 21, 8:43:42 PM Duration: 5.02s
Successfully imported KDC Account Manager credentials.
```
### Screen 6 of 9
#### Kerberos Principal
```
Accept defaults
```
### Screen 7 of 9
#### Configure Ports
```
Accept default ports
Check the box to restart cluster
```
### Screen 8 of 9
#### Enable Kerberos Command
```
Wait for all green
```
### Screen 9 of 9
#### Congratulations

### Received Hue Ticket Renewer error
#### Check Hue Ticket
```
klist -f -c /tmp/hue_krb5_ccache

Ticket cache: FILE:/tmp/hue_krb5_ccache
Default principal: jerry-anderson@LOCAL

Valid starting       Expires              Service principal
09/21/2016 20:55:51  09/22/2016 20:55:51  krbtgt/LOCAL@LOCAL
	Flags: FI
```
```
klist -f -c /tmp/krb5cc_1001

Ticket cache: FILE:/tmp/krb5cc_1001
Default principal: jerry-anderson@LOCAL

Valid starting       Expires              Service principal
09/21/2016 20:55:24  09/22/2016 20:55:24  krbtgt/LOCAL@LOCAL
	Flags: FI
```

#### Fix
```
http://www.cloudera.com/documentation/manager/5-1-x/Configuring-Hadoop-Security-with-Cloudera-Manager/cm5chs_enable_hue_sec_s10.html
```
```
sudo kadmin.local -q "modprinc -maxrenewlife 90day krbtgt/LOCAL"
sudo kadmin.local -q "modprinc -maxrenewlife 90day +allow_renewable hue/ip-172-31-29-173.ec2.internal@LOCAL"
```
# Sentry Lab
## Add Sentry Service
Cluster drop-down -> Add Service -> Sentry

### Select Host 
```
ip-172-31-29-174.ec2.internal
```
### Database Setup
#### Database Host
```
ip-172-31-29-174.ec2.internal
```
#### Database Type
```
MySQL
```
#### Database Name
```
sentry
```
#### Database User
```
sentry
```
#### Database Password
```
sentry
```
#### Test Connection
#### First Run
#### Congratulations
### Disable impersonation for HiveServer2
### Enable Sentry for Hive

# A Quick Sentry Tutorial
###### Create Account and Kerberos Principal
```
sudo useradd sentry_admin
sudo kadmin.local -q "addprinc -pw local sentry_admin@LOCAL"
```
###### Add user to sentry.service.admin.group 
###### Restart Sentry, HUE and Hive
###### Verify User Priveledges
```
sudo su - sentry_admin
kinit
```
```
beeline
!connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-29-174.ec2.internal@LOCAL
```
```
jdbc:hive2://localhost:10000/default> SHOW TABLES;

INFO  : Compiling command(queryId=hive_20160922145757_124939ca-36b7-4a4e-901c-ca6232c6125d): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20160922145757_124939ca-36b7-4a4e-901c-ca6232c6125d); Time taken: 0.698 seconds
INFO  : Executing command(queryId=hive_20160922145757_124939ca-36b7-4a4e-901c-ca6232c6125d): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20160922145757_124939ca-36b7-4a4e-901c-ca6232c6125d); Time taken: 0.249 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.283 seconds)
```
###### Create a Sentry role with full privileges
```
From Beeline

CREATE ROLE sentry_admin;
GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
GRANT ROLE sentry_admin TO GROUP sentry_admin;
SHOW TABLES;
```
```
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
```
###### Create some test users
```
All Hosts

sudo groupadd selector
sudo groupadd inserters
sudo useradd -u 1100 -g selector george
sudo useradd -u 1200 -g inserters ferdinand
```
```
KDC

sudo kadmin.local -q "addprinc -pw george george@LOCAL"
sudo kadmin.local -q "addprinc -pw ferdinand ferdinand@LOCAL"
```
###### Create some test roles
```
From Beeline

CREATE ROLE read_auth;
CREATE ROLE write_auth;
```
###### Grant read privilege to read_auth Role
```
GRANT SELECT ON DATABASE default TO ROLE read_auth;
GRANT ROLE read_auth TO GROUP selector;
```
###### Grant read privilege for default.sample07 only to 'write_auth':
```
REVOKE ALL ON DATABASE default FROM ROLE write_auth;
GRANT SELECT ON default.sample_07 TO ROLE write_auth;
GRANT ROLE write_auth TO GROUP inserters;
```
###### Test as george user
```
kinit

beeline

!connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-29-174.ec2.internal@LOCAL
```
```
SHOW TABLES;

+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
```
###### Test as ferdinand user
```
kinit

beeline

!connect jdbc:hive2://localhost:10000/default;principal=hive/ip-172-31-29-174.ec2.internal@LOCAL
```
```
SHOW TABLES;

+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
```