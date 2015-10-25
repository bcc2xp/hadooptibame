## Install ZooKeeper (@master)
- wget http://ftp.twaren.net/Unix/Web/apache/zookeeper/zookeeper-3.4.6/zookeeper-3.4.6.tar.gz
- tar -zxvf zookeeper-3.4.6.tar.gz
- sudo mv zookeeper-3.4.6 /usr/local/zookeeper
- cp /usr/local/zookeeper/conf/zoo_sample.cfg /usr/local/zookeeper/conf/zoo.cfg

## Modify zoo.cfg (@master)
- vi zoo.cfg

- dataDir=/usr/local/zookeeper 

- server.1=localhost:2888:3888

## Create myid file in /opt/zookeeper (@master)
- vi /usr/local/zookeeper/myid
- 1

## Start ZooKeeper and check (@master)
- /usr/local/zookeeper/bin/zkServer.sh start
- jps