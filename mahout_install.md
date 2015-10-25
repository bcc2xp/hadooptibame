## Install mahout 
- wget http://archive.apache.org/dist/mahout/0.9/mahout-distribution-0.9.tar.gz
- tar -zxvf mahout-distribution-0.9.tar.gz
- mv mahout-distribution-0.9 /usr/local/mahout

## Config variables
- vi ~/.bashrc

export MAHOUT_HOME=/usr/local/mahout

export PATH=$MAHOUT_HOME/bin:$PATH

export MAHOUT_LOCAL=

- source ~/.bashrc

## Check 
- mahout
