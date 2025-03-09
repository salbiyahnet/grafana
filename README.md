# grafana
monitoring

# prometheus
```
wget https://github.com/prometheus/prometheus/releases/download/v3.2.1/prometheus-3.2.1.linux-amd64.tar.gz
```
```
tar xvf prometheus-3.2.1.linux-amd64.tar.gz
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
```
cd /etc/prometheus
#buatkan folder penyimpanan data
```
mkdir /var/lib/prometheus
chown -R prometheus:prometheus /var/lib/prometheus/
```

# node exporter
```
wget https://github.com/prometheus/node_exporter/releases/download/v1.9.0/node_exporter-1.9.0.linux-amd64.tar.gz
```
```
tar xvf node_exporter-1.9.0.linux-amd64.tar.gz
```
