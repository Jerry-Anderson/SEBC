# Storage Labs
## Replicate to another cluster
### Create Source Directory
Creating source directory with Teragen command
### Create Target Directory
```
sudo -u hdfs hdfs dfs -mkdir /sebaacuna
sudo -u hdfs hdfs dfs -chmod 777 /sebaacuna
```
### Generate 500MB Teragen
```
sudo -u hdfs hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen 5000000 /jerry-anderson
```
### Create Peer via Backup menu in CM 
	- Name Peer
	- Enter address to partners name node
	- Enter username and password
	- Test Connection

### Create Backup Schedule
	- Select Source
	- Enter the source directory
	- Select Destination
	- Enter the destination directory
	- Accept remaining Defaults
	- Save schedule

### Backup runs immediately
Job is submitted, but fails due to dns issues between clusters 

## Test HDFS Performance

### Preparation
Create User Directory in HDFS
```
hdfs dfs -mkdir /user/centos
```
```
hdfs dfs -chown centos:centos /user/centos
```
## Teragen
32 MB Block Size / 10 MB File
```
time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Ddfs.block.size=33554432 100000000 /user/centos/terasort-input
```
Time Output
```
real	2m51.855s
user	0m6.462s
sys	0m0.281s
```
## Terasort
### Create cache pool and directive
###### Cache Pool
```
hdfs cacheadmin -addPool terasortPool
```
###### Cache Pool Directive
```
hdfs cacheadmin -addDirective -path /user/centos/terasort-input -pool terasortPool
```
###### View Cache Pool
```
hdfs cacheadmin -listPools -stats terasortPool

NAME          OWNER   GROUP   MODE            LIMIT  MAXTTL  BYTES_NEEDED  BYTES_CACHED  BYTES_OVERLIMIT  FILES_NEEDED  FILES_CACHED
terasortPool  centos  centos  rwxr-xr-x   unlimited   never   10000000000   10000000000                0             3             3
```
### First Run
```
time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort terasort-input terasort-output1
```
```
real	6m57.202s
user	0m9.950s
sys	0m0.413s
```
### Second Run
```
time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort terasort-input terasort-output2
```
```
real	6m59.002s
user	0m9.830s
sys	0m0.386s
```
