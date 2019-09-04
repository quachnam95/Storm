# Storm
## Storm set up
<pre><code>
sudo wget http://mirror.apache-kr.org/storm/apache-storm-2.0.0/apache-storm-2.0.0.tar.gz
mv apache-storm-2.0.0 storm
sudo wget http://mirror.apache-kr.org/zookeeper/zookeeper-3.4.14/zookeeper-3.4.14.tar.gz
mv zookeeper-3.4.14 zookeeper
sudo apt-get install openjdk-8-jdk
sudo apt-get install python

sudo vim .bashrc
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export ZOOKEEPER_HOME=/home/dnslab/zookeeper
export STORM_HOME=/home/dnslab/storm
export PATH=$PATH:$JAVA_HOME/bin:$STORM_HOME/bin:$ZOOKEEPER_HOME/bin

sudo vim /etc/environment
STORM_HOME="/home/dnslab/storm"

cd ~/zookeeper/conf
cp zoo_sample.cfg zoo.cfg
</code></pre>

## Execute Storm
<pre><code>
cd ~/zookeeper/conf
cp zoo_sample.cfg zoo.cfg
cd ~/zookeeper/bin
./zkServer.sh start

cd ~
nohup ./storm/bin/storm nimbus >> nimbus.log 2>&1 &
nohup ./storm/bin/storm supervisor >> supervisor.log 2>&1 &
nohup ./storm/bin/storm ui >> ui.log 2>&1 &
</code></pre>
