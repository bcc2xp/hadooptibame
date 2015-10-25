## Install mahout 
- wget http://ftp.twaren.net/Unix/Web/apache/mahout/0.11.0/apache-mahout-distribution-0.11.0.tar.gz
- tar -zxvf apache-mahout-distribution-0.11.0.tar.gz
- sudo mv apache-mahout-distribution-0.11.0.tar.gz /usr/local/mahout

## Config variables
- vi ~/.bashrc

export MAHOUT_HOME=/usr/local/mahout

export PATH=$MAHOUT_HOME/bin:$PATH

export MAHOUT_LOCAL=

- source ~/.bashrc

## Check 
- mahout
