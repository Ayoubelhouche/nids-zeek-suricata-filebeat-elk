# Suricata Installation and Configuration


## 1. Update package lists and install required packages
```bash
sudo apt-get update
sudo apt-get install software-properties-common
```
## 2. Add the Suricata stable repository
```bash
sudo add-apt-repository ppa:oisf/suricata-stable
```
## 3. Update package lists again and install Suricata
```bash
sudo apt-get update
sudo apt-get install suricata
```
## 4. Open the Suricata configuration file
```bash
sudo nano /etc/suricata/suricata.yaml
```
## 5. Make the following changes in the suricata.yaml file:
#####    i. Change all instances of 'eth0' to your network interface name
#####    ii. Update the 'HOME_NET' variable with your network IP range
#####    iii. Change 'checksum-validation' to 'no' to disable checksum validation

## 6. Save and exit the suricata.yaml file

## 7. Create a systemd service file for Suricata
```bash
sudo nano /lib/systemd/system/suricata.service
```
## 8. Add the following content to the suricata.service file
```
[Unit]
Description=Suricata Intrusion Detection Service
After=syslog.target network-online.target

[Service]
EnvironmentFile=-/etc/default/suricata
EnvironmentFile=-/etc/sysconfig/suricata
ExecStartPre=/bin/rm -f /var/run/suricata.pid
ExecStart=/usr/bin/suricata -c /etc/suricata/suricata.yaml --pidfile /var/run/suricata.pid --af-packet
ExecReload=/bin/kill -USR2 $MAINPID

[Install]
WantedBy=multi-user.target
```

## 9. Save and exit the suricata.service file

## 10. Reload systemd daemon and start Suricata service
```bash
sudo systemctl daemon-reload
sudo systemctl start suricata
```
## 11. Enable Suricata service to start at boot
```bash
sudo systemctl enable suricata
```