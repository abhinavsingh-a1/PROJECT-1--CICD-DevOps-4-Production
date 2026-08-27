
```bash
sudo apt update
```

Links to download Prometheus, Node_Exporter & black Box exporter https://prometheus.io/download/

<img width="1262" height="680" alt="image" src="https://github.com/user-attachments/assets/d0e169a7-0c3a-4920-924f-6d1850fc8f45" />

```bash
wget https://github.com/prometheus/prometheus/releases/download/v3.14.0/prometheus-3.14.0.linux-amd64.tar.gz
```

Extract the package -

```bash
tar -xvf  prometheus-3.14.0.linux-amd64.tar.gz
```

Remove the tar file -

```bash
rm -rf  prometheus-3.14.0.linux-amd64.tar.gz
```

Go inside folder -

```bash
cd  prometheus-3.14.0.linux-amd64
```

Run prometheus in background -
```bash
./prometheus &
```

Once installation is done, run http://public-ip:9090

<img width="1918" height="491" alt="image" src="https://github.com/user-attachments/assets/ca7df166-ba69-4ba4-9464-b6f2b688c93f" />

Prometheus is up & running.

Go to https://prometheus.io/download/
Download bloackbox linux
```bash
wget https://github.com/prometheus/blackbox_exporter/releases/download/v0.28.0/blackbox_exporter-0.28.0.linux-amd64.tar.gz
```

Extract tar file -

```bash
tar -xvf blackbox_exporter-0.28.0.linux-amd64.tar.gz
```

Remove the tar file -

```bash
rm -rf blackbox_exporter-0.28.0.linux-amd64.tar.gz
```

Go inside blackbox folder -

```bash
cd blackbox_exporter-0.28.0.linux-amd64/
```

Start  blackbox -

```bash
./blackbox_exporter &
```

By default it will be running on port 9115 -

run on browser your-public-ip:9115

<img width="418" height="375" alt="image" src="https://github.com/user-attachments/assets/5d79d6ec-4e3e-42e2-82af-15e4f6003a4e" />

Now 

```bash
cd ..
ls
vi prometheus.yml
```

go to https://github.com/prometheus/blackbox_exporter#prometheus-configuration

Copy job_name part only for blackbox -

```yaml
  - job_name: 'blackbox'
    metrics_path: /probe
    params:
      module: [http_2xx]  # Look for a HTTP 200 response.
    static_configs:
      - targets:
        - http://prometheus.io    # Target to probe with http.
        - https://prometheus.io   # Target to probe with https.
        - http://example.com:8080 # Target to probe with http on port 8080.
    relabel_configs:
      - source_labels: [__address__]
        target_label: __param_target
      - source_labels: [__param_target]
        target_label: instance
      - target_label: __address__
        replacement: 127.0.0.1:9115  # The blackbox exporter's real hostname:port.
```

Paste in prometheus.yml file below job_name -

<img width="940" height="781" alt="image" src="https://github.com/user-attachments/assets/4f9b607f-11a9-49d5-b91d-6f737bc3c1c6" />


Replace the public IP address in job_name blackbox
remove the https:// part

Whatever application you want to monitor, you can provide your URL here.
Save and exit

```bash
pgrep prometheus
```


Get prometheus process id
```bash
kill 12345
```

Start prometheus in background -
```bash
./prometheus &
```

Now you can go to prometheus & check target health -

<img width="1914" height="634" alt="image" src="https://github.com/user-attachments/assets/d5393894-7f04-4f90-a77f-26e948cfc59e" />

You can see, both blockbox endpoint are up.








































# Install Grafana -

Links to download Grafana https://grafana.com/grafana/download

Execute below command given on website -

<img width="1605" height="627" alt="image" src="https://github.com/user-attachments/assets/3940f5bf-fb4a-4041-9af2-1eab9040036f" />

After complete installation -

```bash
### You can start grafana-server by executing
 sudo /bin/systemctl start grafana-server
```

run on browser -

https://your-public-ip:3000

<img width="1494" height="774" alt="image" src="https://github.com/user-attachments/assets/eab3c2a6-38af-43a9-bdba-aa8d4cc08df2" />

default login : admin
password : admin


# Add Prometheus inside Grafana

Goto connections >> data sources

<img width="1301" height="531" alt="image" src="https://github.com/user-attachments/assets/d6e961fb-c352-491e-8342-b6fea4c5aa52" />

Select prometheus & provide the URL of prometheus -

<img width="1887" height="799" alt="image" src="https://github.com/user-attachments/assets/00b66514-99b1-430d-afa1-1dad5ca46e8a" />

Once done, click on Save & test and it will immediately tell you the status of connection.

<img width="1116" height="256" alt="image" src="https://github.com/user-attachments/assets/07492896-7247-48e8-bd0a-b5ff93224fa2" />

# Import dashboard

Search for dahsboard grafana blackbox in google, go to website and copy ID -

<img width="1741" height="744" alt="image" src="https://github.com/user-attachments/assets/05476aba-da05-433f-8e33-009808868b52" />

Paste in Grafana, load & import dashboard -

<img width="1183" height="825" alt="image" src="https://github.com/user-attachments/assets/c67c4c26-0809-4d2f-963c-bb26130b5e8d" />

You can see the website we are monitoring, its status, probe everything -

<img width="1518" height="922" alt="image" src="https://github.com/user-attachments/assets/49750287-0587-432d-a9d5-4a246c10653b" />




# Blackbox

Now go and refresh blackbox URL -

<img width="921" height="954" alt="image" src="https://github.com/user-attachments/assets/8bed46b7-d28c-4a24-9e37-4cebd1399bb8" />





# Lets Monitor system metrics of Jenkins

Go to Jenkins >> Plugins >> Available PlugIns

Select Prometheus Metrics & Install & RESTART Jenkins

GO to https://prometheus.io/download/

Node exporter & copy linux one -

<img width="1339" height="311" alt="image" src="https://github.com/user-attachments/assets/5b4acb99-2622-48f4-8a26-d829b297db2c" />

Download the package for Jenkins in Jenkin server -

```bash
wget https://github.com/prometheus/node_exporter/releases/download/v1.12.1/node_exporter-1.12.1.linux-amd64.tar.gz
```

Extract package -

```bash
tar -xvf node_exporter-1.12.1.linux-amd64.tar.gz
```

Remove package -

```bash
rm -rf node_exporter-1.12.1.linux-amd64.tar.gz
```

Go inside folder

```bash
 cd node_exporter-1.12.1.linux-amd64/
```

Run the node exporter -

```bash
./node_exporter &
```

Run node exporter on browser

https://public-ip-of-jenkins-server:9100

<img width="756" height="515" alt="image" src="https://github.com/user-attachments/assets/a15bb91c-23eb-4dc1-b4ea-99c6d291a914" />

If you click on metrics, you will get everything.

```bash
pgrep prometheus
kill process_id
```

Now go to prometheus.yml

Add below -

```yaml
  - job_name: "node_exporter"
    static_configs:
      - targets: ["54.165.96.212:8080"]

  - job_name: "jenkins"
    metrics_path: "/Prometheus"
    static_configs:
      - targets: ["54.165.96.212:9100"]
```

```bash
./prometheus &
```

It will start prometheus.

You can see everythins is up and running -

<img width="1916" height="885" alt="image" src="https://github.com/user-attachments/assets/d6a8009a-6633-456c-8485-1a83e7e8daf6" />


Lets add the Node Exporter dashboard -

# Add Node Exporter dashboard -

Search for node exporter dashboard -

Copy dashboard id & paste in grafana -

Load & Import the dashboard -

Node exporter dashboard will be added.

<img width="1912" height="721" alt="image" src="https://github.com/user-attachments/assets/35e6bcf3-7d0c-4e31-aa72-109940dfb425" />


































































































































