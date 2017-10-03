####################
# Disabled SELINUX #
####################
vi /etc/selinux/config
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disabled
# SELINUXTYPE= can take one of three two values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected.
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted


a.- getenforce
output: "Disabled"

###############
# Install CM  #
###############

1.- cat /proc/sys/vm/swappiness
output:"30"

1.-a echo "1" > /proc/sys/vm/swappiness

2.-  echo "vm.swappiness = 1" >> /etc/sysctl.conf

3.- df -h
output: "
Filesystem                 Size  Used Avail Use% Mounted on
/dev/mapper/rootvg-rootlv  7.8G   69M  7.3G   1% /
devtmpfs                    16G     0   16G   0% /dev
tmpfs                       16G     0   16G   0% /dev/shm
tmpfs                       16G  8.4M   16G   1% /run
tmpfs                       16G     0   16G   0% /sys/fs/cgroup
/dev/mapper/rootvg-usrlv   9.8G  1.1G  8.2G  11% /usr
/dev/mapper/rootvg-varlv   7.8G  101M  7.3G   2% /var
/dev/mapper/rootvg-tmplv   2.0G  6.1M  1.8G   1% /tmp
/dev/mapper/rootvg-homelv  976M  2.6M  907M   1% /home
/dev/mapper/rootvg-optlv   2.0G  6.1M  1.8G   1% /opt
/dev/sda1                  976M   60M  849M   7% /boot
/dev/sdb1                   63G   53M   60G   1% /mnt/resource
tmpfs                      3.2G     0  3.2G   0% /run/user/1000
/dev/sdc                    79G   57M   75G   1% /data01
/dev/sdd                    79G   60M   75G   1% /data02"


4.- echo never > /sys/kernel/mm/transparent_hugepage/enabled
4.b.- echo never > /sys/kernel/mm/transparent_hugepage/defrag

5.-
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.1.5  netmask 255.255.255.0  broadcast 10.0.1.255
        inet6 fe80::20d:3aff:fef9:cf67  prefixlen 64  scopeid 0x20<link>
        ether 00:0d:3a:f9:cf:67  txqueuelen 1000  (Ethernet)
        RX packets 12144  bytes 6137455 (5.8 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16904  bytes 2783435 (2.6 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

6.-  
echo "10.0.1.8  clouderab1 clouderab1.bootcamp.cmp" >> /etc/hosts
echo "10.0.1.5  clouderab2 clouderab2.bootcamp.cmp" >> /etc/hosts
echo "10.0.1.6  clouderab3 clouderab3.bootcamp.cmp" >> /etc/hosts
echo "10.0.1.7  clouderab4 clouderab4.bootcamp.cmp" >> /etc/hosts

/etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
10.0.1.4  clouderab1 clouderab1.bootcamp.cmp
10.0.1.5  clouderab2 clouderab2.bootcamp.cmp
10.0.1.6  clouderab3 clouderab3.bootcamp.cmp
10.0.1.7  clouderab4 clouderab4.bootcamp.cmp


7.-
yum install -y ntp
yum install -y nscd

[root@clouderab2 kudaw]# service nscd status
Redirecting to /bin/systemctl status nscd.service
? nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-10-02 18:18:30 UTC; 3s ago
  Process: 2708 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 2709 (nscd)
   CGroup: /system.slice/nscd.service
           +-2709 /usr/sbin/nscd

Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring directory `/etc` (2)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring file `/etc/hosts` (4)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring directory `/etc` (2)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring file `/etc/resolv.conf` (5) Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring directory `/etc` (2)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring file `/etc/services` (6)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring directory `/etc` (2)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 disabled inotify-based monitoring ...ry

Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 stat failed for file `/etc/netgrou...ry

Oct 02 18:18:30 clouderab2 systemd[1]: Started Name Service Cache Daemon.
Hint: Some lines were ellipsized, use -l to show in full.


[root@clouderab2 kudaw]# service nscd status
Redirecting to /bin/systemctl status nscd.service
? nscd.service - Name Service Cache Daemon
   Loaded: loaded (/usr/lib/systemd/system/nscd.service; disabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-10-02 18:18:30 UTC; 3s ago
  Process: 2708 ExecStart=/usr/sbin/nscd $NSCD_OPTIONS (code=exited, status=0/SUCCESS)
 Main PID: 2709 (nscd)
   CGroup: /system.slice/nscd.service
           +-2709 /usr/sbin/nscd

Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring directory `/etc` (2)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring file `/etc/hosts` (4)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring directory `/etc` (2)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring file `/etc/resolv.conf` (5) Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring directory `/etc` (2)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring file `/etc/services` (6)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 monitoring directory `/etc` (2)
Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 disabled inotify-based monitoring ...ry

Oct 02 18:18:30 clouderab2 nscd[2709]: 2709 stat failed for file `/etc/netgrou...ry

Oct 02 18:18:30 clouderab2 systemd[1]: Started Name Service Cache Daemon.
Hint: Some lines were ellipsized, use -l to show in full.
[root@clouderab2 kudaw]# service ntpd status
Redirecting to /bin/systemctl status ntpd.service
? ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; disabled; vendor preset: disabled)
   Active: inactive (dead)



#########
# MYSQL #     
#########
1.a.- wget https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm
1.b.- sudo rpm -ivh mysql57-community-release-el7-11.noarch.rpm
1.c.- yum install -y mysql-server
1.d.- sudo systemctl start mysqld
1.e.- service mysqld restart
1.f.-
 sudo systemctl status mysqld
? mysqld.service - MySQL Server
   Loaded: loaded (/usr/lib/systemd/system/mysqld.service; enabled; vendor preset: disabled)
   Active: active (running) since Mon 2017-10-02 20:11:55 UTC; 2min 22s ago
     Docs: man:mysqld(8)
           http://dev.mysql.com/doc/refman/en/using-systemd.html
  Process: 6142 ExecStart=/usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid $MYSQLD_OPTS (code=exited, status=0/SUCCESS)
  Process: 6050 ExecStartPre=/usr/bin/mysqld_pre_systemd (code=exited, status=0/SUCCESS)
 Main PID: 6144 (mysqld)
   CGroup: /system.slice/mysqld.service
           +-6144 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld...

Oct 02 20:11:14 clouderab4 systemd[1]: Starting MySQL Server...
Oct 02 20:11:55 clouderab4 systemd[1]: Started MySQL Server.

###################################
#  Path B install using CM 5.9.x  #
###################################

1.- sudo yum install java-1.7.0-openjdk-devel

2.- wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.44.tar.gz
2.b.- tar zxvf mysql-connector-java-5.1.44.tar.gz
2.c.-  cp mysql-connector-java-5.1.44/mysql-connector-java-5.1.44-bin.jar /usr/share/java/mysql-connector-java.jar 



3.-
Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database oozie default character set utf8;
Query OK, 1 row affected (0.00 sec)

mysql>  grant all privileges on oozie.* to 'oozie'@'localhost' identified by 'oozie';
ERROR 1819 (HY000): Your password does not satisfy the current policy requirements
mysql> uninstall plugin validate_password;
Query OK, 0 rows affected (0.01 sec)

mysql>  grant all privileges on oozie.* to 'oozie'@'localhost' identified by 'oozie';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql>  grant all privileges on oozie.* to 'oozie'@'%' identified by 'oozie';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> create database amon DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> create database rman DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> create database metastore DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> create database sentry DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> create database nav DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> create database navms DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

mysql> grant all on amon.* TO 'amon'@'%' IDENTIFIED BY 'amon_password';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman_password';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> grant all on metastore.* TO 'hive'@'%' IDENTIFIED BY 'hive_password';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'sentry_password';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> grant all on nav.* TO 'nav'@'%' IDENTIFIED BY 'nav_password';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql>  grant all on navms.* TO 'navms'@'%' IDENTIFIED BY 'navms_password';
Query OK, 0 rows affected, 1 warning (0.00 sec)



4.- yum localinstall cloudera-manager-daemons-5.11.2-1.cm5112.p0.6.el7.x86_64.rpm