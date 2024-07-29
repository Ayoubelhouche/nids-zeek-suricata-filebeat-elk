# Zeek Installation Steps
## 1. Add the Elastic GPG Key
```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
```
## 2. Add the Elastic Repository
```bash
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
```
## 3. Install Filebeat
```bash
sudo apt update
sudo apt-get install filebeat
```
## 4. Configure Filebeat

Edit the 
```bash 
/etc/filebeat/filebeat.yml file
```
and make the following changes:

For Kibana host:

`setup.kibana:
host: "localhost:5601"`

For Elasticsearch:

`output.elasticsearch:
hosts: ["localhost:9200"]`

## 5. Enable Zeek and Suricata Modules
```bash
sudo filebeat modules enable zeek
sudo filebeat modules enable suricata
```

## 6. Configure Module Files
Zeek Module

```bash
sudo nano /etc/filebeat/modules.d/zeek.yml
```

Add the following line at the end of the file:

`
var.paths: ["/opt/zeek/logs/current/*.log"]
`

Suricata Module

```bash
sudo nano /etc/filebeat/modules.d/suricata.yml
```

Add the following line at the end of the file:

`
var.paths: ["/var/log/suricata/eve.json"]
`

## 7. Start and Enable Filebeat Service
```bash
sudo systemctl start filebeat
sudo systemctl enable filebeat
```