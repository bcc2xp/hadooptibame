## Install HBase (@master)
- wget http://ftp.tc.edu.tw/pub/Apache/hbase/0.98.15/hbase-0.98.15-hadoop2-bin.tar.gz
- tar -zxvf hbase-0.98.15-hadoop2-bin.tar.gz
- sudo mv hbase-0.98.15-hadoop2 /usr/local/hbase
- vi /usr/local/hbase/conf/hbase-env.sh

export HBASE_MANAGES_ZK=false


## Create ZooKeeper folder for Hbase (@master)
- mkdir /home/hadoop/zookeeper

### Overwrite hbase-site.xml (@master)
- vi /usr/local/hbase/conf/hbase-site.xml
- view hbase-site.xml (https://github.com/ywchiu/hadooptibame/blob/master/hbase-site.xml)

### Create hbase folder in HDFS (@master)
- hadoop fs -mkdir /hbase

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