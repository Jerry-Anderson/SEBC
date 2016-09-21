# Determining mapreduce.job.maps

http://stackoverflow.com/questions/30003268/yarn-maximum-parallel-map-task-count

```
mapreduce.job.maps = MIN(yarn.nodemanager.resource.memory-mb / mapreduce.map.memory.mb,yarn.nodemanager.resource.cpu-vcores / mapreduce.map.cpu.vcores, number of physical drives x workload factor) x number of worker nodes
```

### Number of worker nodes = 10
### Min = 24
## mapreduce.job.maps = 240

### 111616 / 1024 = 109
yarn.nodemanager.resource.memory-mb = 111616

mapreduce.map.memory.mb = 1024


### 64 / 1 = 64
yarn.nodemanager.resource.cpu-vcores = 64

mapreduce.map.cpu.vcores = 1

### 12 * 2 = 24
number of physical drives = 12

workload factor = 2


