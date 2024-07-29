# ZEEK INSTALLATION STEPS

## 1. Install Prerequisites
Before installing Zeek, you need to install the required dependencies. On Ubuntu, you can install them with the following command:

```bash
sudo apt-get install cmake make gcc g++ flex bison libpcap-dev libssl-dev python3-dev python3-devel swig zlib1g-dev
```

## 2. Download Zeek
Go to the website: https://software.opensuse.org/download.html?project=security%3Azeek&package=zeek

Pick your OS and version, and copy the provided commands to download and install Zeek.

## 3. Verify Installation
After completing the installation steps correctly, you should find Zeek installed in `/opt/zeek/bin`.

## 4. Edit Configuration Files

### 4.1 Configure Networks
```bash
sudo nano /opt/zeek/etc/networks.cfg
```
Add your network IP and prefix in the `Networks` section.

### 4.2 Configure Interface
```bash
sudo nano /opt/zeek/etc/node.cfg
```
Change the `interface` value to your network interface name. You can find the interface name with the command `ip a`.

### 4.3 Configure Logging
```bash
sudo nano /opt/zeek/etc/zeekctl.cfg
```
Take note of where Zeek saves the logs, which should be `/opt/zeek/logs`. In a production environment, you may want to configure log rotation to manage disk space.

### 4.4 Configure JSON Logging
```bash
sudo nano /opt/zeek/share/zeek/site/local.zeek
```
Add the following line to configure Zeek to produce logs in JSON format, which is useful for integration with tools like Filebeat and Elasticsearch:


` @load policy/tuning/json-logs.zeek `


## 5. Deploy and Enable Zeek
Deploy and enable Zeek with the following command:

```bash
sudo zeekctl deploy
```

You can check the status with:

```bash
sudo zeekctl status
```

If you run into problems, try:

```bash
export PATH=$PATH:/opt/zeek/bin
source ~/.bashrc
```

After completing these steps, Zeek should be installed and configured on your system.