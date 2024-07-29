
![header](docs/title.png)

# Intrusion Detection with Zeek, Suricata, Filebeat, Elasticsearch, and Kibana

## Overview

This project sets up an Intrusion Detection System (IDS) using Zeek and Suricata to monitor network traffic, Filebeat to collect and ship logs to Elasticsearch, and Kibana to visualize the data.

## Features

- Easy-to-follow steps
- Using Zeek for detailed logs
- Using Suricata for coherent logs in JSON format (highly compatible with ELK stack)
- Utilizing Filebeat and Elasticsearch compatibility
- Kibana integration with Elasticsearch for illustrative visualizations

## Installation

To set up the environment, please follow the guide step-by-step.

## Note

I have set up everything on a single node, which is suitable for testing and learning purposes. For commercial or professional use of this project, separating these components is recommended. This allows for better resource management, improved security, and the ability to scale each component independently as needed.

### Potential Challenges for Single Node Setup

- **Resource Contention:** If the VM is underpowered, these components might compete for resources, leading to performance degradation.
- **Security Risks:** Running Suricata on the same VM as other sensitive applications could create a single point of failure.
- **Scalability:** As your data volume and network traffic grow,
