# Storm
## Storm set up
<pre><code>
sudo wget http://mirror.apache-kr.org/storm/apache-storm-2.0.0/apache-storm-2.0.0.tar.gz
tar -zxvf apache-storm-2.0.0.tar.gz
mv apache-storm-2.0.0 /usr/local/storm
sudo wget http://mirror.apache-kr.org/zookeeper/zookeeper-3.4.14/zookeeper-3.4.14.tar.gz
tar -zxvf zookeeper-3.4.14
mv zookeeper-3.4.14 /usr/local/zookeeper
sudo apt-get install openjdk-8-jdk
sudo apt-get install python

sudo vim .bashrc
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export ZOOKEEPER_HOME=/home/dnslab/zookeeper
export STORM_HOME=/home/dnslab/storm
export PATH=$PATH:$JAVA_HOME/bin:$STORM_HOME/bin:$ZOOKEEPER_HOME/bin

sudo vim /etc/environment
STORM_HOME="/usr/local/storm"

cd ~/zookeeper/conf
cp zoo_sample.cfg zoo.cfg
</code></pre>

## Execute Storm
<pre><code>
cd ~/zookeeper/conf
cp zoo_sample.cfg zoo.cfg
cd ~/zookeeper/bin
./zkServer.sh start

cd /usr/local/storm
./storm nimbus &
./storm supervisor &
./storm ui &
</code></pre>
