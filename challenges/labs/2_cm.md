# Contents /etc/yum/repos.d (Trick?)
```
[centos@ip-172-31-26-227 yum.repos.d]$ ll /etc/yum/repos.d
ls: cannot access /etc/yum/repos.d: No such file or directory
```
# Contents /etc/yum.repos.d

```
[centos@ip-172-31-26-227 yum.repos.d]$ ll /etc/yum.repos.d/
total 36
-rw-r--r--. 1 root root 1664 Dec  9  2015 CentOS-Base.repo
-rw-r--r--. 1 root root 1309 Dec  9  2015 CentOS-CR.repo
-rw-r--r--. 1 root root  649 Dec  9  2015 CentOS-Debuginfo.repo
-rw-r--r--. 1 root root  290 Dec  9  2015 CentOS-fasttrack.repo
-rw-r--r--. 1 root root  630 Dec  9  2015 CentOS-Media.repo
-rw-r--r--. 1 root root 1331 Dec  9  2015 CentOS-Sources.repo
-rw-r--r--. 1 root root 1952 Dec  9  2015 CentOS-Vault.repo
-rw-r--r--  1 root root  294 Sep 23 14:07 cloudera-manager.repo
-rw-r--r--  1 root root 1416 Sep 23 13:39 mysql-community.repo
```
# Grant Statement
```
grant all on scm.* TO 'scm'@'ip-172-31-26-227.ec2.internal' IDENTIFIED BY 'scm';```
# Start Cloudera Manager
```
[centos@ip-172-31-26-227 ~]$ sudo head -1 /var/log/cloudera-scm-server/cloudera-scm-server.log
2016-09-23 14:48:45,694 INFO main:com.cloudera.server.cmf.Main: Starting SCM Server. JVM Args: [-Dlog4j.configuration=file:/etc/cloudera-scm-server/log4j.properties, -Dfile.encoding=UTF-8, -Dcmf.root.logger=INFO,LOGFILE, -Dcmf.log.dir=/var/log/cloudera-scm-server, -Dcmf.log.file=cloudera-scm-server.log, -Dcmf.jetty.threshhold=WARN, -Dcmf.schema.dir=/usr/share/cmf/schema, -Djava.awt.headless=true, -Djava.net.preferIPv4Stack=true, -Dpython.home=/usr/share/cmf/python, -XX:+UseConcMarkSweepGC, -XX:+UseParNewGC, -XX:+HeapDumpOnOutOfMemoryError, -Xmx2G, -XX:MaxPermSize=256m, -XX:+HeapDumpOnOutOfMemoryError, -XX:HeapDumpPath=/tmp, -XX:OnOutOfMemoryError=kill -9 %p], Args: [], Version: 5.8.0 (#42 built by jenkins on 20160714-1246 git: d08ac14ff050a108864fab00205c12e0d4043132)

[centos@ip-172-31-26-227 ~]$ sudo grep "Started Jetty server" /var/log/cloudera-scm-server/cloudera-scm-server.log
2016-09-23 14:49:55,893 INFO WebServerImpl:com.cloudera.server.cmf.WebServerImpl: Started Jetty server.
```
