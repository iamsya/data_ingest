# Sqoop Exercies
1.
```
[training@localhost ~]$ sqoop import --connect jdbc:mysql://localhost/loudacre --username training --password training \
> --table accounts \
> --columns "acct_num,first_name,last_name" \
> --target-dir /loudacre/accounts/user_info \
> --fields-terminated-by "\t"
19/04/07 22:59:44 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 22:59:44 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 22:59:44 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 22:59:44 INFO tool.CodeGenTool: Beginning code generation
19/04/07 22:59:45 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 22:59:45 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 22:59:45 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/f58f7433a763a8a67702bff7f9ff35f1/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 22:59:47 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/f58f7433a763a8a67702bff7f9ff35f1/accounts.jar
19/04/07 22:59:47 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 22:59:47 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 22:59:47 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 22:59:47 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 22:59:47 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 22:59:47 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 22:59:48 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 22:59:48 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 22:59:48 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 22:59:50 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 22:59:50 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/04/07 22:59:50 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/04/07 22:59:50 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 22:59:50 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554698677356_0003
19/04/07 22:59:51 INFO impl.YarnClientImpl: Submitted application application_1554698677356_0003
19/04/07 22:59:51 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554698677356_0003/
19/04/07 22:59:51 INFO mapreduce.Job: Running job: job_1554698677356_0003
19/04/07 22:59:59 INFO mapreduce.Job: Job job_1554698677356_0003 running in uber mode : false
19/04/07 22:59:59 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 23:00:05 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 23:00:11 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 23:00:16 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 23:00:22 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 23:00:22 INFO mapreduce.Job: Job job_1554698677356_0003 completed successfully
19/04/07 23:00:22 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=560464
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=2615920
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=16991
		Total vcore-seconds taken by all map tasks=16991
		Total megabyte-seconds taken by all map tasks=4349696
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=433
		CPU time spent (ms)=3560
		Physical memory (bytes) snapshot=499339264
		Virtual memory (bytes) snapshot=8262041600
		Total committed heap usage (bytes)=251920384
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=2615920
19/04/07 23:00:22 INFO mapreduce.ImportJobBase: Transferred 2.4947 MB in 34.0934 seconds (74.9297 KB/sec)
19/04/07 23:00:22 INFO mapreduce.ImportJobBase: Retrieved 129761 records.


```

2. 
```
[training@localhost ~]$ sqoop import --connect jdbc:mysql://localhost/loudacre --username training --password training --table accounts --target-dir /loudacre/accounts/user_compressed --compression-codec org.apache.hadoop.io.compress.SnappyCodec --as-parquetfile
19/04/07 23:27:43 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 23:27:44 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 23:27:44 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 23:27:44 INFO tool.CodeGenTool: Beginning code generation
19/04/07 23:27:44 INFO tool.CodeGenTool: Will generate java class as codegen_accounts
19/04/07 23:27:44 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:27:44 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:27:44 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/104bd94e31b7ed98b56d03864075080d/codegen_accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 23:27:47 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/104bd94e31b7ed98b56d03864075080d/codegen_accounts.jar
19/04/07 23:27:47 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 23:27:47 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 23:27:47 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 23:27:47 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 23:27:47 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 23:27:47 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 23:27:47 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 23:27:48 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:27:48 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:27:49 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 23:27:50 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 23:27:52 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 23:27:52 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/04/07 23:27:52 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/04/07 23:27:52 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 23:27:52 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554698677356_0004
19/04/07 23:27:52 INFO impl.YarnClientImpl: Submitted application application_1554698677356_0004
19/04/07 23:27:52 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554698677356_0004/
19/04/07 23:27:52 INFO mapreduce.Job: Running job: job_1554698677356_0004
19/04/07 23:28:00 INFO mapreduce.Job: Job job_1554698677356_0004 running in uber mode : false
19/04/07 23:28:00 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 23:28:10 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 23:28:18 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 23:28:25 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 23:28:32 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 23:28:32 INFO mapreduce.Job: Job job_1554698677356_0004 completed successfully
19/04/07 23:28:32 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=569280
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=65906
		HDFS: Number of bytes written=5904609
		HDFS: Number of read operations=272
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=40
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=26092
		Total vcore-seconds taken by all map tasks=26092
		Total megabyte-seconds taken by all map tasks=6679552
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1197
		CPU time spent (ms)=12870
		Physical memory (bytes) snapshot=739491840
		Virtual memory (bytes) snapshot=8296509440
		Total committed heap usage (bytes)=251920384
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=0
19/04/07 23:28:32 INFO mapreduce.ImportJobBase: Transferred 5.6311 MB in 42.7179 seconds (134.9837 KB/sec)
19/04/07 23:28:32 INFO mapreduce.ImportJobBase: Retrieved 129761 records.
```

3.
```
[training@localhost ~]$ sqoop import --connect jdbc:mysql://localhost/loudacre --table accounts --target-dir /loudacre/accounts/CA --compression-codec org.apache.hadoop.io.compress.SnappyCodec --as-avrodatafile --username training --password training
19/04/07 23:41:51 INFO sqoop.Sqoop: Running Sqoop version: 1.4.6-cdh5.7.0
19/04/07 23:41:51 WARN tool.BaseSqoopTool: Setting your password on the command-line is insecure. Consider using -P instead.
19/04/07 23:41:52 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
19/04/07 23:41:52 INFO tool.CodeGenTool: Beginning code generation
19/04/07 23:41:52 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:41:52 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:41:52 INFO orm.CompilationManager: HADOOP_MAPRED_HOME is /usr/lib/hadoop-mapreduce
Note: /tmp/sqoop-training/compile/4674025c4381cd8033f69fdb51759826/accounts.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
19/04/07 23:41:54 INFO orm.CompilationManager: Writing jar file: /tmp/sqoop-training/compile/4674025c4381cd8033f69fdb51759826/accounts.jar
19/04/07 23:41:54 WARN manager.MySQLManager: It looks like you are importing from mysql.
19/04/07 23:41:54 WARN manager.MySQLManager: This transfer can be faster! Use the --direct
19/04/07 23:41:54 WARN manager.MySQLManager: option to exercise a MySQL-specific fast path.
19/04/07 23:41:54 INFO manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
19/04/07 23:41:54 INFO mapreduce.ImportJobBase: Beginning import of accounts
19/04/07 23:41:54 INFO Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
19/04/07 23:41:54 INFO Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
19/04/07 23:41:55 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:41:55 INFO manager.SqlManager: Executing SQL statement: SELECT t.* FROM `accounts` AS t LIMIT 1
19/04/07 23:41:55 INFO mapreduce.DataDrivenImportJob: Writing Avro schema file: /tmp/sqoop-training/compile/4674025c4381cd8033f69fdb51759826/accounts.avsc
19/04/07 23:41:56 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
19/04/07 23:41:56 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
19/04/07 23:41:58 INFO db.DBInputFormat: Using read commited transaction isolation
19/04/07 23:41:58 INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(`acct_num`), MAX(`acct_num`) FROM `accounts`
19/04/07 23:41:58 INFO db.IntegerSplitter: Split size: 32440; Num splits: 4 from: 1 to: 129761
19/04/07 23:41:58 INFO mapreduce.JobSubmitter: number of splits:4
19/04/07 23:41:58 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1554698677356_0005
19/04/07 23:41:59 INFO impl.YarnClientImpl: Submitted application application_1554698677356_0005
19/04/07 23:41:59 INFO mapreduce.Job: The url to track the job: http://localhost:8088/proxy/application_1554698677356_0005/
19/04/07 23:41:59 INFO mapreduce.Job: Running job: job_1554698677356_0005
19/04/07 23:42:06 INFO mapreduce.Job: Job job_1554698677356_0005 running in uber mode : false
19/04/07 23:42:06 INFO mapreduce.Job:  map 0% reduce 0%
19/04/07 23:42:14 INFO mapreduce.Job:  map 25% reduce 0%
19/04/07 23:42:20 INFO mapreduce.Job:  map 50% reduce 0%
19/04/07 23:42:27 INFO mapreduce.Job:  map 75% reduce 0%
19/04/07 23:42:34 INFO mapreduce.Job:  map 100% reduce 0%
19/04/07 23:42:34 INFO mapreduce.Job: Job job_1554698677356_0005 completed successfully
19/04/07 23:42:34 INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=565772
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=470
		HDFS: Number of bytes written=8008341
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=0
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=21150
		Total vcore-seconds taken by all map tasks=21150
		Total megabyte-seconds taken by all map tasks=5414400
	Map-Reduce Framework
		Map input records=129761
		Map output records=129761
		Input split bytes=470
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=419
		CPU time spent (ms)=10870
		Physical memory (bytes) snapshot=609214464
		Virtual memory (bytes) snapshot=8283324416
		Total committed heap usage (bytes)=251920384
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=8008341
19/04/07 23:42:34 INFO mapreduce.ImportJobBase: Transferred 7.6373 MB in 38.4711 seconds (203.2864 KB/sec)
19/04/07 23:42:34 INFO mapreduce.ImportJobBase: Retrieved 129761 records.
```