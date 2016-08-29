# Elasticsearch_Logstash_Kibana Installation Tutorial

```
sudo add-apt-repository -y ppa:webupd8team/java
sudo apt-get update
sudo apt-get -y install oracle-java8-installer
wget -qO - https://packages.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
echo "deb http://packages.elastic.co/elasticsearch/2.x/debian stable main" | sudo tee -a /etc/apt/sources.list.d/elasticsearch-2.x.list
sudo apt-get update
sudo apt-get -y install elasticsearch
sudo vi /etc/elasticsearch/elasticsearch.yml
```
replace its value with "localhost" so it looks like this
network.host: localhost
Save and exit elasticsearch.yml
```
sudo service elasticsearch restart
sudo update-rc.d elasticsearch defaults 95 10
sudo groupadd -g 999 kibana
sudo useradd -u 999 -g 999 kibana
cd ~; wget https://download.elastic.co/kibana/kibana/kibana-4.2.0-linux-x64.tar.gz
tar xvf kibana-*.tar.gz
```
find the line that specifies server.host, and replace the IP address ("0.0.0.0" by default) with "localhost"
```
sudo mkdir -p /opt/kibana
sudo cp -R ~/kibana-4*/* /opt/kibana/
sudo chown -R kibana: /opt/kibana
cd /etc/init.d && sudo curl -o kibana https://gist.githubusercontent.com/thisismitch/8b15ac909aed214ad04a/raw/fc5025c3fc499ad8262aff34ba7fde8c87ead7c0/kibana-4.x-init
cd /etc/default && sudo curl -o kibana https://gist.githubusercontent.com/thisismitch/8b15ac909aed214ad04a/raw/fc5025c3fc499ad8262aff34ba7fde8c87ead7c0/kibana-4.x-default
```
Now enable the Kibana service
```
sudo chmod +x /etc/init.d/kibana
sudo update-rc.d kibana defaults 96 9
sudo service kibana start
```
https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-14-04
