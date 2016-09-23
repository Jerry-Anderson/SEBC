# DB Grants
```
grant all on hive.* TO 'hive'@'%' IDENTIFIED BY 'hive';
grant all on oozie.* to 'oozie'@'%' identified by 'oozie';
grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman';
```

# Hive
```
mysql> show grants for hive;
+-----------------------------------------------------------------------------------------------------+
| Grants for hive@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'hive'@'%' IDENTIFIED BY PASSWORD '*4DF1D66463C18D44E3B001A8FB1BBFBEA13E27FC' |
| GRANT ALL PRIVILEGES ON `hive`.* TO 'hive'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)
```
# RMAN
```
mysql> show grants for rman;
+-----------------------------------------------------------------------------------------------------+
| Grants for rman@%                                                                                   |
+-----------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'rman'@'%' IDENTIFIED BY PASSWORD '*819397F8B454D58DA4E9F42A88A4873756B8C96D' |
| GRANT ALL PRIVILEGES ON `rman`.* TO 'rman'@'%'                                                      |
+-----------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)
```
# Oozie
```
mysql> show grants for oozie;
+------------------------------------------------------------------------------------------------------+
| Grants for oozie@%                                                                                   |
+------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'oozie'@'%' IDENTIFIED BY PASSWORD '*2B03FE0359FAD3B80620490CE614F8622E0828CD' |
| GRANT ALL PRIVILEGES ON `oozie`.* TO 'oozie'@'%'                                                     |
+------------------------------------------------------------------------------------------------------+
2 rows in set (0.00 sec)
```
# HDFS /user Directory
```
[centos@ip-172-31-26-226 ~]$ hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - christie christie          0 2016-09-23 15:38 /user/christie
drwxrwxrwx   - mapred   hadoop            0 2016-09-23 15:34 /user/history
drwxrwxr-t   - hive     hive              0 2016-09-23 15:35 /user/hive
drwxrwxr-x   - hue      hue               0 2016-09-23 15:35 /user/hue
drwxrwxr-x   - oozie    oozie             0 2016-09-23 15:35 /user/oozie
drwxr-xr-x   - weiner   weiner            0 2016-09-23 15:38 /user/weiner
```
# Hadoop Classpath
```
[centos@ip-172-31-26-226 ~]$ hadoop classpath
/etc/hadoop/conf:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop/lib/*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop/.//*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-hdfs/./:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-hdfs/lib/*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-hdfs/.//*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-yarn/lib/*:/opt/cloudera/parcels/CDH-5.7.3-1.cdh5.7.3.p0.5/lib/hadoop/libexec/../../hadoop-yarn/.//*:/opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/lib/*:/opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/.//*
```
# API Output
```
{
  "items" : [ {
    "hostId" : "i-021be4e9eacfdeac8",
    "ipAddress" : "172.31.26.226",
    "hostname" : "ip-172-31-26-226.ec2.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-172-31-26-227.ec2.internal:7180/cmf/hostRedirect/i-021be4e9eacfdeac8",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, 
```