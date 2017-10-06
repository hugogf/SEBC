provider: AWS

public IP              internal IP         hostname -f                      Release
54.237.239.51          172.30.2.80         ip-172-30-2-80.ec2.internal       CentOS Linux release 7.3.1611 (Core)
54.237.206.189         172.30.2.69         ip-172-30-2-69.ec2.internal       CentOS Linux release 7.3.1611 (Core)
34.207.77.187          172.30.2.189        ip-172-30-2-189.ec2.internal      CentOS Linux release 7.3.1611 (Core)
54.146.172.197         172.30.2.62         ip-172-30-2-62.ec2.internal       CentOS Linux release 7.3.1611 (Core)

ip-172-30-2-80 / ip-172-30-2-80.ec2.internal
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       20G  1.5G   19G   8% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
/dev/xvdb        79G   57M   75G   1% /data01
/dev/xvdc        79G   57M   75G   1% /data02
tmpfs           1.5G     0  1.5G   0% /run/user/0


[root@ip-172-30-2-80 yum.repos.d]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.net.cen.ct.gov
 * extras: mirror.lug.udel.edu
 * updates: mirror.wdc1.us.leaseweb.net

repo id                                            repo name                                             status

base/7/x86_64                                      CentOS-7 - Base                                       9,591 
extras/7/x86_64                                    CentOS-7 - Extras                                       225 
updates/7/x86_64                                   CentOS-7 - Updates                                      731 
repolist: 10,547


saturn:x:2800:2800::/home/saturn:/bin/bash
haley:x:2900:2900::/home/haley:/bin/bash

comets:x:2901:haley
planets:x:2902:saturn
