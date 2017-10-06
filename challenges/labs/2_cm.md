[root@ip-172-30-2-69 cloudera-scm-server]# ls -l /etc/yum.repos.d
total 36
-rw-r--r-- 1 root root 1664 Aug 30 15:53 CentOS-Base.repo
-rw-r--r-- 1 root root 1309 Aug 30 15:53 CentOS-CR.repo
-rw-r--r-- 1 root root  649 Aug 30 15:53 CentOS-Debuginfo.repo
-rw-r--r-- 1 root root  314 Aug 30 15:53 CentOS-fasttrack.repo
-rw-r--r-- 1 root root  630 Aug 30 15:53 CentOS-Media.repo
-rw-r--r-- 1 root root 1331 Aug 30 15:53 CentOS-Sources.repo
-rw-r--r-- 1 root root 3830 Aug 30 15:53 CentOS-Vault.repo
-rw-r--r-- 1 root root 1838 Apr 27 09:14 mysql-community.repo
-rw-r--r-- 1 root root 1885 Apr 27 09:14 mysql-community-source.repo


[root@ip-172-30-2-69 cloudera-scm-server]# /usr/share/cmf/schema/scm_prepare_database.sh mysql -h 54.237.239.51 scm scm scm
JAVA_HOME=/usr/lib/jvm/java-openjdk
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/lib/jvm/java-openjdk/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
Fri Oct 06 12:53:07 UTC 2017 WARN: Establishing SSL connection without server's identity verification is not recommended. According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set. For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'. You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!