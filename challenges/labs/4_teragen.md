[root@ip-172-30-2-80 hadoop-0.20-mapreduce]# time sudo -u saturn hadoop jar hadoop-examples.jar teragen -Ddfs.block.size=33554432 -Dmapreduce.map.memory.mb=512  65536000 tgen
17/10/06 14:24:15 INFO client.RMProxy: Connecting to ResourceManager at ip-172-30-2-189.ec2.internal/172.30.2.189:8032
17/10/06 14:24:15 INFO terasort.TeraSort: Generating 65536000 using 2
17/10/06 14:24:15 INFO mapreduce.JobSubmitter: number of splits:2
17/10/06 14:24:15 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/10/06 14:24:15 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1507296701918_0002
17/10/06 14:24:16 INFO impl.YarnClientImpl: Submitted application application_1507296701918_0002
17/10/06 14:24:16 INFO mapreduce.Job: The url to track the job: http://ip-172-30-2-189.ec2.internal:8088/proxy/application_1507296701918_0002/
17/10/06 14:24:16 INFO mapreduce.Job: Running job: job_1507296701918_0002
17/10/06 14:24:22 INFO mapreduce.Job: Job job_1507296701918_0002 running in uber mode : false
17/10/06 14:24:22 INFO mapreduce.Job:  map 0% reduce 0%
17/10/06 14:24:33 INFO mapreduce.Job:  map 12% reduce 0%
17/10/06 14:24:36 INFO mapreduce.Job:  map 18% reduce 0%
17/10/06 14:24:39 INFO mapreduce.Job:  map 19% reduce 0%
17/10/06 14:24:42 INFO mapreduce.Job:  map 20% reduce 0%
17/10/06 14:24:54 INFO mapreduce.Job:  map 22% reduce 0%
17/10/06 14:25:00 INFO mapreduce.Job:  map 23% reduce 0%
17/10/06 14:25:09 INFO mapreduce.Job:  map 33% reduce 0%
17/10/06 14:25:12 INFO mapreduce.Job:  map 37% reduce 0%
17/10/06 14:25:15 INFO mapreduce.Job:  map 38% reduce 0%
17/10/06 14:25:30 INFO mapreduce.Job:  map 39% reduce 0%
17/10/06 14:25:33 INFO mapreduce.Job:  map 40% reduce 0%
17/10/06 14:25:42 INFO mapreduce.Job:  map 48% reduce 0%
17/10/06 14:25:45 INFO mapreduce.Job:  map 49% reduce 0%
17/10/06 14:25:48 INFO mapreduce.Job:  map 51% reduce 0%
17/10/06 14:25:51 INFO mapreduce.Job:  map 54% reduce 0%
17/10/06 14:25:54 INFO mapreduce.Job:  map 58% reduce 0%
17/10/06 14:25:57 INFO mapreduce.Job:  map 59% reduce 0%
17/10/06 14:26:15 INFO mapreduce.Job:  map 67% reduce 0%
17/10/06 14:26:18 INFO mapreduce.Job:  map 70% reduce 0%
17/10/06 14:26:21 INFO mapreduce.Job:  map 73% reduce 0%
17/10/06 14:26:34 INFO mapreduce.Job:  map 74% reduce 0%
17/10/06 14:26:43 INFO mapreduce.Job:  map 76% reduce 0%
17/10/06 14:26:46 INFO mapreduce.Job:  map 83% reduce 0%
17/10/06 14:26:49 INFO mapreduce.Job:  map 87% reduce 0%
17/10/06 14:26:52 INFO mapreduce.Job:  map 89% reduce 0%
17/10/06 14:26:58 INFO mapreduce.Job:  map 90% reduce 0%
17/10/06 14:27:01 INFO mapreduce.Job:  map 91% reduce 0%
17/10/06 14:27:10 INFO mapreduce.Job:  map 92% reduce 0%
17/10/06 14:27:13 INFO mapreduce.Job:  map 93% reduce 0%
17/10/06 14:27:17 INFO mapreduce.Job:  map 94% reduce 0%
17/10/06 14:27:28 INFO mapreduce.Job:  map 95% reduce 0%
17/10/06 14:27:31 INFO mapreduce.Job:  map 97% reduce 0%
17/10/06 14:27:32 INFO mapreduce.Job:  map 99% reduce 0%
17/10/06 14:27:35 INFO mapreduce.Job:  map 100% reduce 0%
17/10/06 14:27:35 INFO mapreduce.Job: Job job_1507296701918_0002 completed successfully
17/10/06 14:27:35 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=245234
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=170
                HDFS: Number of bytes written=6553600000
                HDFS: Number of read operations=8
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=4
        Job Counters
                Launched map tasks=2
                Other local map tasks=2
                Total time spent by all maps in occupied slots (ms)=380976
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=380976
                Total vcore-seconds taken by all map tasks=380976
                Total megabyte-seconds taken by all map tasks=390119424
        Map-Reduce Framework
                Map input records=65536000
                Map output records=65536000
                Input split bytes=170
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=969
                CPU time spent (ms)=102250
                Physical memory (bytes) snapshot=342159360
                Virtual memory (bytes) snapshot=2279714816
                Total committed heap usage (bytes)=430440448
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=140750829423462787
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=6553600000

real    3m22.859s
user    0m6.534s
sys     0m0.319s



[root@ip-172-30-2-80 hadoop-0.20-mapreduce]# hdfs dfs -ls /user/saturn/tgen
Found 3 items
-rw-r--r--   3 saturn planets          0 2017-10-06 14:27 /user/saturn/tgen/_SUCCESS
-rw-r--r--   3 saturn planets 3276800000 2017-10-06 14:27 /user/saturn/tgen/part-m-00000
-rw-r--r--   3 saturn planets 3276800000 2017-10-06 14:27 /user/saturn/tgen/part-m-00001



[root@ip-172-30-2-80 hadoop-0.20-mapreduce]# sudo -u saturn hadoop fsck -blocks /user/saturn
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.

Connecting to namenode via http://ip-172-30-2-62.ec2.internal:50070
FSCK started by saturn (auth:SIMPLE) from /172.30.2.80 for path /user/saturn at Fri Oct 06 14:30:20 UTC 2017
..........Status: HEALTHY
 Total size:    6554117825 B
 Total dirs:    4
 Total files:   10
 Total symlinks:                0
 Total blocks (validated):      203 (avg. block size 32286294 B)
 Minimally replicated blocks:   203 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     2.9802957
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Fri Oct 06 14:30:20 UTC 2017 in 11 milliseconds


The filesystem under path '/user/saturn' is HEALTHY