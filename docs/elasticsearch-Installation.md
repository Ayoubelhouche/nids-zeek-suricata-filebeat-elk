# Elasticsearch Installation Steps

## 1. Install Elasticsearch
```bash
sudo apt-get update
sudo apt-get install elasticsearch
```

## 2. Configure Elasticsearch

Open the configuration file for editing:
```bash
sudo nano /etc/elasticsearch/elasticsearch.yml
```

- `cluster.name: "choose_a_name_for_your_cluster"`
- `node.name: "choose_a_name_for_your_current_node"`
- `network.host: 0.0.0.0`
  - This setting allows Elasticsearch to bind to all available network interfaces. For production environments, it's recommended to specify the appropriate IP address or hostname instead of using `0.0.0.0`.
- `http.port: 9200`
- `discovery.seed_hosts: ["127.0.0.1", "[::1]"]`
  - This setting specifies the initial list of master-eligible nodes to perform discovery when new nodes are started.
- `cluster.initial_master_nodes: ["put_here_the_name_of_the_node_you_chose"]`
  - This setting specifies the list of master-eligible nodes to start the cluster with. It should match the `node.name` you chose earlier.
- `xpack.security.enabled: false`
- `xpack.security.enrollment.enabled: false`

For the other lines, don't change anything.
Making a copy of this file before modifying it is a good practice.

## 3. Activate Elasticsearch
```bash
sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch
sudo systemctl status elasticsearch
```

## 4. Additional Options

- Enable or disable the X-Pack security feature
  - In newer versions of Elasticsearch, security features are enabled by default. However, for testing purposes on a local machine and network, disabling security is acceptable.
  - If security is enabled or disabled, modify the `filebeat.yml` file accordingly to ensure proper communication with Elasticsearch.

Please note that disabling security features is not recommended for production environments accessible from the internet or untrusted networks. In such cases, it is essential to configure and enable security measures to protect your Elasticsearch cluster and data.

## 5. Elasticsearch Directory and Files

- The Elasticsearch installation directory is usually located at `/usr/share/elasticsearch`.
- The configuration files are stored in `/etc/elasticsearch`.
- Log files are located in `/var/log/elasticsearch`.
- Data files are stored in `/var/lib/elasticsearch`.

It's a good practice to monitor the log files for any errors or warnings during the installation and configuration process.

