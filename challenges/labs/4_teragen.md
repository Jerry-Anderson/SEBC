# Teragen Command
```
[christie@ip-172-31-26-226 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Ddfs.block.size=64000000 51200000 tgen64
```
# Time
```
real	1m21.656s
user	0m5.703s
sys  	0m0.295s
```
# HDFS
```
[christie@ip-172-31-26-226 ~]$ hdfs dfs -ls /user/christie/tgen64
Found 3 items
-rw-r--r--   3 christie christie          0 2016-09-23 15:56 /user/christie/tgen64/_SUCCESS
-rw-r--r--   3 christie christie 2560000000 2016-09-23 15:56 /user/christie/tgen64/part-m-00000
-rw-r--r--   3 christie christie 2560000000 2016-09-23 15:56 /user/christie/tgen64/part-m-00001
```
# Blocks
```
[christie@ip-172-31-26-226 ~]$ hdfs fsck -blocks /user/christie/tgen64
Connecting to namenode via http://ip-172-31-26-226.ec2.internal:50070
FSCK started by christie (auth:SIMPLE) from /172.31.26.226 for path /user/christie/tgen64 at Fri Sep 23 16:02:25 UTC 2016
...Status: HEALTHY
 Total size:	5120000000 B
 Total dirs:	1
 Total files:	3
 Total symlinks:		0
 Total blocks (validated):	80 (avg. block size 64000000 B)
 Minimally replicated blocks:	80 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Fri Sep 23 16:02:25 UTC 2016 in 5 milliseconds


The filesystem under path '/user/christie/tgen64' is HEALTHY
```