 spark-submit --class org.apache.spark.examples.SparkPi \
     --master yarn \
     --deploy-mode cluster \
     lib/spark-examples*.jar \
     10


WARNING: User-defined SPARK_HOME (/data01/cloudera/parcels/CDH-5.9.0-1.cdh5.9.0.p0.23/lib/spark) overrides detected (/data01/cloudera/parcels/CDH-5.11.2-1.cdh5.11.2.p0.4/lib/spark).
WARNING: Running spark-class from user-defined location.