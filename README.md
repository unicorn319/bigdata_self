# bigdata_self
This is a repository for recording and moving files for course of big data.

## session summary

 1. Use cloudera vm as primary project host system
  - as we discussed and did experiment on MacOS, Windows Os and cloudera CentOS, we reached agreement to choose cloudera vm as our primary project host system. Main reasons including cloudera vm is compatible across all platforms. Services provided by cloudera are fruitful (hbase, hdfs, zookeeper. etc.). To install any other services are much easier on cloudera vm.

 2. keep use python 2.6 on cloudera vm
 - for current status, please keep python2.6 to launch web related services(crawler, flask)
 - use command 'sudo easy_install BeautifulSoup' to install bs4 module for web crawler.
 - install flask before you run app.py file
 - if you want to install python 2.7 and install pip with 2.7 you can use [this tutorial](http://www.lecloud.net/post/61401763496/install-update-to-python-27-and-latest-pip-on)  

 3. sync up with new github code for crawler
 - found a bug and fixed with https://github.com/dataengineerterm3/WebCrawler please use newest code for web crawler 
 - use 'python crawler.app' to start crawler service 

 4. restart redis service when needed
- use [this tutorial](http://business-it-consultant.co.uk/blog/install-redis-centos-6) to install redis on 

 5. install and execute storm service 
 - use 'storm jar target/Storm-Redis-PubSub-0.0.1-SNAPSHOT-jar-with-dependencies.jar storm.RedisPubSubTopology'
- use 'python app.py' to launch web service and remember to put '127.0.0.1/stream' to your browser to trigger background listen action

### steps to install storm on cloudera-vm
open terminal in cloudera-VM

```
mkdir storm
sudo wget  http://mirror.23media.de/apache/storm/apache-storm-0.9.5/apache-storm-0.9.5.tar.gz
sudo tar -xvzf apache-storm-0.9.5.tar.gz
cd apache-storm-0.9.5
export STORM_HOME=/home/cloudera/storm/apache-storm-0.9.5
export PATH=$PATH:$STORM_HOME/bin
storm version
```

##setup storm on your own vm 

 1. `sudo adduser --system storm `
 2. `sudo groupadd storm `
 3. `sudo usermod -a -G storm storm `
 4. `sudo chown -R storm:storm /home/cloudera/storm`
 5. `sudo chmod 775 /home/cloudera/`
 6. `mkdir storm`
 7. `cd storm`
 8. `sudo wget http://mirror.23media.de/apache/storm/apache-storm-0.9.5/apache-storm-0.9.5.tar.gz`
 9. `sudo tar -xvzf apache-storm-0.9.5.tar.gz`
 10.  `sudo nano /home/cloudera/storm/apache-storm-0.9.5/conf/storm.yaml`
 11. paste following text, save and exit, command control+X and type ':wq' + enter

 ########### These MUST be filled in for a storm configuration
storm.zookeeper.servers:
 - zkserver1

nimbus.host: nimbus1


 12. then we need to set storm command globally 
  `sudo vi ~/.bashrc`
  
 -- then paste following two lines
  `export STORM_HOME=/home/cloudera/storm/apache-storm-0.9.5`
 `.export PATH=$PATH:$STORM_HOME/bin`

13. `source ~/.bashrc`

