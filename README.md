# grafana
Tutorial by mas Aji Diyantoro
```
https://youtu.be/M6ds-70GIpY?si=QJUku3UPyR4brc3N
```

# prometheus
```
wget https://github.com/prometheus/prometheus/releases/download/v2.37.6/prometheus-2.37.6.linux-amd64.tar.gz
```
```
tar xvfz prometheus-*.tar.gz
```
# buatkan user untuk prometheus
```
sudo groupadd --system prometheus
sudo useradd --system -s /sbin/nologin -g prometheus prometheus
```
# pindahkan binary file prometheus dan promtool ke /usr/local/bin
```
sudo mv prometheus promtool /usr/local/bin/
which prometheus
```
#pindahkan file config .yaml
```
mkdir /etc/prometheus
mv prometheus.yml
mv consoles/ console_libraries/ /etc/prometheus/
```
cd /etc/prometheus
#buatkan folder penyimpanan data
```
mkdir /var/lib/prometheus
chown -R prometheus:prometheus /var/lib/prometheus/
```
set background services
nano /etc/systemd/system/prometheus.service
```
[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
Group=prometheus
Type=simple
Restart=on-failure
RestartSec=5s
ExecStart=/usr/local/bin/prometheus \
    --config.file /etc/prometheus/prometheus.yml \
    --storage.tsdb.path /var/lib/prometheus/ \
    --web.console.templates=/etc/prometheus/consoles \
    --web.console.libraries=/etc/prometheus/console_libraries \
    --web.listen-address=0.0.0.0:9090 \
    --web.enable-lifecycle \
    --log.level=info

[Install]
WantedBy=multi-user.target
```
```
sudo systemctl daemon-reload
sudo systemctl enable prometheus
sudo systemctl start prometheus
sudo systemctl status prometheus
```
# node exporter
```
wget https://github.com/prometheus/node_exporter/releases/download/v1.9.0/node_exporter-1.9.0.linux-amd64.tar.gz
```
```
tar xvf node_exporter-1.9.0.linux-amd64.tar.gz
```
