# Linux Configuration Checks
## Initial Setup
	- Record local ip addresses in a file for scripting
	- Setup SSH Keys across the cluster with Master 1 Private Key
###### Disable SELinux after next reboot
```
sudo vim /etc/selinux/config
```
###### Set SELinux to Permissive Immediately
```
sudo setenforce 0
```
### Install Packages
	- sudo yum install -y nscd ntp vim wget bind-utils telnet
### VM.SWAPPINESS
	- created /etc/sysctl.d/cloudera_sysctl.conf
	  vm.swappiness=1 
	- sudo cp /tmp/cloudera_sysctl.conf /etc/sysctl.d/
	- sudo sysctl -p
	- sudo sysctl vm.swappiness=1
### Disable Transparent Huge Pages
	- sudo bash -c "echo never > /sys/kernel/mm/transparent_hugepage/enabled"
	- sudo bash -c "echo never > /sys/kernel/mm/transparent_hugepage/defrag"
###### Disable at boot
```
Add to end of /etc/rc.d/rc.local

#disable THP at boot time
if test -f /sys/kernel/mm/transparent_hugepage/enabled; then
  echo never > /sys/kernel/mm/transparent_hugepage/enabled
fi
if test -f /sys/kernel/mm/transparent_hugepage/defrag; then
  echo never > /sys/kernel/mm/transparent_hugepage/defrag
fi
```
### NOATIME
	- currently not using a non root volume
### Reserve Space
	- currently not using a non root volume
### Max File and Processes
	- created /etc/security/limits.d/cloudera_limits.conf
	  hdfs   - nofile 32768
	  hdfs   - nproc  32768
	  mapred - nofile 32768
	  mapred - nproc  32768
	  hbase  - nofile 32768
	  hbase  - nproc  32768
	- sudo cp /tmp/cloudera_limits.conf /etc/security/limits.d/
### Forward / Reverse Lookup
	- host ip-172-31-29-173
	- host 172.31.29.173
	- host ip-172-31-29-174
	- host 172.31.29.174
	- host ip-172-31-29-175
	- host 172.31.29.175
	- host ip-172-31-29-176
	- host 172.31.29.176
	- host ip-172-31-29-177
	- host 172.31.29.177
### Start and Enable Services
	- sudo systemctl start nscd.service
	- sudo systemctl enable nscd.service
	- sudo systemctl start ntpd.service
	- sudo systemctl enable ntpd.service

	One Command
	sudo systemctl start nscd.service;sudo systemctl enable nscd.service;sudo systemctl start ntpd.service;sudo systemctl enable ntpd.service
### Verify Services Start and Enable 
	- sudo systemctl is-enabled ntpd.service
	- sudo systemctl status ntpd.service
	- sudo nscd -g
	- sudo systemctl is-enabled ntpd.service
	- sudo systemctl status ntpd.service

