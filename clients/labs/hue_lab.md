# Authenticate using Linux users/groups
###### Add User (All Hosts)
```
sudo useradd -u 1300 hue_test1 
```
###### Export variable to point at correct DB
```
export HUE_CONF_DIR="/var/run/cloudera-scm-agent/process/`ls -alrt /var/run/cloudera-scm-agent/process | grep HUE | tail -1 | awk '{print $9}'`"
export HUE_IGNORE_PASSWORD_SCRIPT_ERRORS=1  
export JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera 
/opt/cloudera/parcels/CDH/lib/hue/build/env/bin/hue useradmin_sync_with_unix
```
# Integrate Hue and Sentry
#### Check Settings and ensure hue user
sentry.service.admin.group
sentry.service.allow.connect

###### Put hue user in sentry admin role group on OS
sudo useradd -G -a sentry_admin hue_test1
** Note ** 
ALL SERVERS

###### Run User Sync
sudo HUE_DATABASE_PASSWORD=hue HUE_IGNORE_PASSWORD_SCRIPT_ERRORS=1  JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera HUE_SECRET_KEY=admin HUE_CONF_DIR=/var/run/cloudera-scm-agent/process/211-hue-HUE_SERVER /opt/cloudera/parcels/CDH/lib/hue/build/env/bin/hue useradmin_sync_with_unix

###### Verify hue_test1 can view roles in Hue
# Hue HA
```
https://www.cloudera.com/documentation/enterprise/5-5-x/topics/cdh_hag_hue_config.html#concept_cn1_nhn_j5
```
Hue -> Instances -> Add Role Instance
Select Additional Hue Server
Select Kerberos Ticket Renewer
Select Hue LB

New Kerberos Ticket Renewer didn't start
	- Couldn't use Hue keytab on new host (Master 2)
```
Deleted /tmp/hue_cache on Master 2
Restarted service