## install flume

- wget http://ftp.twaren.net/Unix/Web/apache/flume/1.6.0/apache-flume-1.6.0-bin.tar.gz
- tar -zxvf apache-flume-1.6.0-bin.tar.gz
- sudo mv apache-flume-1.6.0-bin /usr/local/flume


### gedit ~/.bashrc

export FLUME_HOME=/usr/local/flume
export FLUME_CONF_DIR=$FLUME_HOME/conf
export PATH=$PATH:$FLUME_HOME/bin