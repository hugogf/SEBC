mysql> show variables where Variable_name like '%host%';
+-------------------------------+----------------+
| Variable_name                 | Value          |
+-------------------------------+----------------+
| host_cache_size               | 279            |
| hostname                      | ip-172-30-2-80 |
| performance_schema_hosts_size | -1             |
| report_host                   |                |
+-------------------------------+----------------+

[root@ip-172-30-2-80 ~]# mysql --version
mysql  Ver 14.14 Distrib 5.7.19, for Linux (x86_64) using  EditLine wrapper


mysql>  show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sys                |
+--------------------+