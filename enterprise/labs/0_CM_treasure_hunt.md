# CM Monitoring Lab

##What is ubertask optimization?
```
Ubertask optimization means that the ApplicationMaster uses its own JVM to run Map and Reduce tasks, so the tasks are executed sequentially on one node. YARN only has to allocate a container for ApplicationMaster.
```
##Where in CM is the Kerberos Security Realm value displayed?
```
Administration Menu -> Settings -> Kerberos Security Realm (defaul_realm)
```

##Which CDH service(s) host a property for enabling Kerberos authentication?
```
Zookeeper
Hive
Oozie
HDFS
Hue
```

##How do you upgrade the CM agents?
```
From the Hosts page -> Select the Re-Run Upgrade Wizard button
```

##Give the tsquery statement used to chart Hue's CPU utilization?
```
SELECT cpu_percent WHERE roleType = HUE_SERVER
```

##Name all the roles that make up the Hive service
```
Gateway
Hive Metastore Server
HiveServer2
```

##What steps must be completed before integrating Cloudera Manager with Kerberos?
Prerequisites

```
Functioning KDC
Secure Communication between Agents and Servers

Inside CM, use the Cluster drop-down to select enable Kerberos.  This will launch the kerberos wizard to fill in the details about the KDC.
```