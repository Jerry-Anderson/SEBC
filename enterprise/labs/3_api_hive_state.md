# Restart Hive
```
curl -X POST -u admin:admin 'http://localhost:7180/api/v12/clusters/Jerry-Anderson/services/hive/commands/rstart'
```
```
{
  "id" : 426,
  "name" : "Restart",
  "startTime" : "2016-09-21T19:26:28.055Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
```
