## Install HBase (@master)
- wget http://apache.stu.edu.tw/hbase/0.98.15/hbase-0.98.15-hadoop2-bin.tar.gz
- tar -zxvf hbase-0.98.15-hadoop2-bin.tar.gz
- sudo mv hbase-0.98.15-hadoop2 /usr/local/hbase
- vi /usr/local/hbase/conf/hbase-env.sh

-- export JAVA_HOME=/usr/bin/java

-- export HBASE_MANAGES_ZK=false


## Create ZooKeeper folder for Hbase (@master)
- mkdir /home/zookeeper

### Overwrite hbase-site.xml (@master)
- vi /usr/local/hbase/conf/hbase-site.xml
- <?xml version="1.0"?> <configuration> <property> <name>hbase.rootdir</name> <value>hdfs://localhost:9000/hbase</value> </property> 
- <property> <name>hbase.master</name> <value>hdfs://localhost:60000</value> </property> 
- <property> <name>hbase.cluster.distributed</name> <value>true</value> </property> 
- <property> <name>hbase.zookeeper.property.clientPort</name> <value>2181</value> </property> 
- <property> <name>hbase.zookeeper.quorum</name> <value>master</value> </property> 
- <property> <name>hbase.zookeeper.property.dataDir</name> <value>/home/zookeeper</value> </property> 
- <property> <name>hbase.client.scanner.caching</name> <value>200</value> </property> 
- <property> <name>hbase.balancer.period</name> <value>300000</value> </property> 
- <property> <name>hbase.client.write.buffer</name> <value>10485760</value> </property> 
- <property> <name>hbase.hregion.majorcompaction</name> <value>7200000</value> </property> 
- <property> <name>hbase.hregion.max.filesize</name> <value>67108864</value> </property> 
- <property> <name>hbase.hregion.memstore.flush.size</name> <value>1048576</value> </property> 
- <property> <name>hbase.server.thread.wakefrequency</name> <value>30000</value> </property> 
- </configuration>

### Create hbase folder in HDFS (@master)
¡Vhadoop fs -mkdir /hbase

## Setup HBase slavers (@master)
- vi /usr/local/hbase/conf/regionservers

localhost

## Config variables (@master, @slaver1, @slaver2)
- vi /etc/profile
- export HBASE_HOME=/usr/local/hbase
- export PATH=$PATH:$HBASE_HOME/bin
- source /etc/profile

## Remove slf4j (bug) (@master)
- rm /usr/local/hbase/lib/slf4j-log4j12-1.6.4.jar

## Start hbase (@master)
- start-hbase.sh
- stop-hbase.sh

## Check in browser (in your PC)
- HBase: http://localhost:60010/master-status

## Start HBase thrift service (@master)
- /usr/local/hbase/bin/hbase thrift start -threadpool

## Create Hbase database
- create 'Contacts', 'Personal', 'Office¡¥
- list
- put 'Contacts', '1000', 'Personal:Name', 'John Dole'
- put 'Contacts', '1000', 'Personal:Phone', '1-425-000-0001'
- put 'Contacts', '1000', 'Office:Phone', '1-425-000-0002'
- put 'Contacts', '1000', 'Office:Address', '1111 San Gabriel Dr.'
- scan 'Contacts'

## Start HBase restful API
- /usr/local/hbase/bin/hbase rest start
- http://localhost:8080/version
¡V http://localhost:8080/Contacts/schema