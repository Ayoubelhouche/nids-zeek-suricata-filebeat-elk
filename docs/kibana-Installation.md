# Kibana Installation Steps

Kibana is a powerful open-source data visualization and exploration tool that works seamlessly with Elasticsearch. It provides a user-friendly web interface for searching, analyzing, and visualizing data stored in an Elasticsearch cluster.

## 1. Install Kibana

```bash
sudo apt-get update
sudo apt install kibana -y
```

## 2. Configure Kibana
Edit the Kibana Configuration File:

```bash
sudo nano /etc/kibana/kibana.yml
```

- `server.port: 5601` - The port on which Kibana will run (default is 5601).
- `server.host: "localhost"` - The hostname or IP address on which Kibana will listen for incoming requests. Set it to `0.0.0.0` to allow access from any IP address.
- `elasticsearch.hosts: ["http://localhost:9200"]` - The URL(s) of the Elasticsearch instance(s) to which Kibana will connect.

You can modify these settings according to your specific requirements.

## 3. Activate Kibana
```bash
sudo systemctl start kibana
sudo systemctl enable kibana
sudo systemctl status kibana
```

In newer versions of Kibana, security features are enabled by default, and you may need to configure a service token to access Kibana. However, for testing purposes on a local machine and network, you can disable security and access Kibana without a service token.

Please note that disabling security features is not recommended for production environments accessible from the internet or untrusted networks. In such cases, it is essential to configure and enable security measures to protect your Elasticsearch and Kibana setup.

If security is enabled, you will need to generate and configure a service token for Kibana to communicate with Elasticsearch. The process for generating and configuring the service token may vary depending on the version of Elasticsearch and Kibana you are using. Consult the official documentation for the specific steps.

## 4. Access Kibana
Once Kibana is running, you can access the web interface by opening a web browser and navigating to `http://localhost:5601` (or the appropriate IP address and port if you modified the configuration).

