
## 1.1 Install docker

Before running the scripts, run `docker-install.sh` on EC2 instance to install Docker.

# Docker Setup

```bash
chmod +x docker-install.sh
./docker-install.sh
```

# Jenkins Nexus Setup
```bash
sudo su
docker compose -p nexus up -d
```

# Install Java
```bash
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
```

# Install Trivy
Follow official website for commands - https://trivy.dev/docs/latest/getting-started/installation/
```bash
sudo apt-get install wget gnupg
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb generic main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy
```

# Run Jenkins

Lets check containers -

```bash
docker ps
```

<img width="1429" height="54" alt="image" src="https://github.com/user-attachments/assets/3f17116b-1f85-4bf7-960f-a225797f17a9" />

Get public IP of EC2 instance -
```bash
curl ifconfig.me
```

Copy IP address and place it with port 8080. Get UI of Jenkins -

<img width="964" height="427" alt="image" src="https://github.com/user-attachments/assets/e7c3762e-8e12-4d08-8c18-d6e6498135b7" />

Get initial password string of Jenkins, copy string and paste in password - 

```bash
docker logs jenkins
```

<img width="1655" height="681" alt="image" src="https://github.com/user-attachments/assets/e5e3a6ec-0744-4657-8ec4-0cebabeba34b" />

<img width="983" height="899" alt="image" src="https://github.com/user-attachments/assets/7dc49a17-7427-4162-8cca-7345c22e93c9" />

<img width="990" height="829" alt="image" src="https://github.com/user-attachments/assets/12b1a0f7-c5e7-4225-b1c4-5b6df13dac23" />

# Install Jenkins Plugins
Check Nexus-Jenkins-Installation >> INSTALL-JENKINS-PLUGINS.md



# Once plugins successfully install, configure them.<br/>

<br/>
Go to Manage Jenkins >> Tools >> Configure the tools -<br/>

<img width="1335" height="398" alt="image" src="https://github.com/user-attachments/assets/705238f2-ab29-437e-8cb1-2b09f0f3aa56" /><br/><br/><br/>

<img width="1357" height="496" alt="image" src="https://github.com/user-attachments/assets/b8770795-89b9-467b-a733-567b7194db2b" />

<br/>Click Apply.
<br/>
<br/>

# Lets create pipeline -

<br/>
Click on New Item -<br/>
<img width="963" height="412" alt="image" src="https://github.com/user-attachments/assets/6919d3be-b439-4c00-a547-ef7cbb86af18" /><br/><br/>

<img width="807" height="835" alt="image" src="https://github.com/user-attachments/assets/1c678eb3-ba47-4c35-9f26-6300352655ab" />

<br/>Click Ok
<br/><br/>
<br/>Go to Pipeline >> Configure >>
<br/>
<img width="514" height="502" alt="image" src="https://github.com/user-attachments/assets/9f56476c-5e06-44ae-b0bb-7801d89aade6" /><br/>
<br/>
Under pipeline section, select Hello World & copy & paste multiple sections of Hello World -<br/>
<br/>
<img width="1299" height="708" alt="image" src="https://github.com/user-attachments/assets/ff2804de-e096-4e99-8113-b9321d309c51" /><br/>
<br/>

# Go to Pipeline >> README.md
Check complete process for creating pipeline from scratch.


