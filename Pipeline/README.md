<br/>
Click on New Item -<br/>
<img width="963" height="412" alt="image" src="https://github.com/user-attachments/assets/6919d3be-b439-4c00-a547-ef7cbb86af18" /><br/><br/>

<img width="807" height="835" alt="image" src="https://github.com/user-attachments/assets/1c678eb3-ba47-4c35-9f26-6300352655ab" />
<br/>Click Ok
<br/><br/>
<br/>Go to Pipeline >> Configure >>
<br/>
<img width="1201" height="593" alt="image" src="https://github.com/user-attachments/assets/0a9a0d8f-1001-45a3-8fc0-6aabeeb30cb7" />

<br/>
Under pipeline section, select Hello World & copy & paste multiple sections of Hello World -<br/>
<br/>
<img width="1304" height="575" alt="image" src="https://github.com/user-attachments/assets/ba048df6-cb0a-4bdd-9bd2-388dc8aba9d3" />
<br/>


Lets start writing Pipeline -
<br/><br/>
<br/><br/>

# Stage 1: Git CheckOut

Add tools & first stage Git Checkout -
<br/>
<img width="1302" height="617" alt="image" src="https://github.com/user-attachments/assets/32766e60-bb2e-4900-99f2-14a8f2df1fb7" />

<br/>Use Pipeline syntex to create snippet.

## ADD CREDENTIAL FOR GITHUB IN JENKINS. FOLLOW -
### Credentials >> Jenkins >> Add-Credentials.md

<br/>Select git, paste repo URL, And add credentials with username & password -
<br/>
<img width="1531" height="788" alt="image" src="https://github.com/user-attachments/assets/7ffc6b40-c792-4bab-ad57-fced2f73354e" />

<br/>Click on generate pipeline script -

<br/><img width="1319" height="716" alt="image" src="https://github.com/user-attachments/assets/7d6770de-c481-4a59-96dd-9eaa42875e5d" />

<br/>Copy syntax and paste in pipeline under steps.
<br/>
<img width="1183" height="399" alt="image" src="https://github.com/user-attachments/assets/ac5181ea-0ccd-4a39-a437-6e35f2bb26a2" />

# Stage 2 & 3: Compile & Test

<img width="1281" height="204" alt="image" src="https://github.com/user-attachments/assets/b9f533d8-3184-474e-b0a5-376e8841a01a" />


<br/><br/>

# Stage 4 : File system scan

### It will scan current directory and export report in table format in html file -

<img width="1268" height="106" alt="image" src="https://github.com/user-attachments/assets/b7efe064-b585-419f-aee9-0dd774ee30b4" />

# Stage 5 : SonarQube Analysis

# Create credential for Sonarqube in Jenkins<br/>
## Check Credential >> Jenkins >> ADD-SONARQUBE-TOKEN-IN-JENKINS-CREDENTIAL.md

<br/>
Lets go back to pipeline syntax -
<br/>
<img width="1322" height="521" alt="image" src="https://github.com/user-attachments/assets/782a5b3a-5c65-491e-9cd3-c866ef47fd48" />

<br/>
Paste syntax in pipeline. <br/>
<br/>
Why I have replaced credentialsId: Sonar-token ==>> Sonar
<br/>
Because in Jenkins >> System, we have installed Sonar server with name of Sonar. There we have provided URL & password.
<br/>

Now lets make changes. To call Sonar scanner tool, we have to define it -

<img width="1311" height="225" alt="image" src="https://github.com/user-attachments/assets/fa663e76-a430-4b9c-88ca-1f4a55ed25fd" />

<br/>
<img width="1234" height="528" alt="image" src="https://github.com/user-attachments/assets/079a7fbe-eae9-41b9-837b-ca2b060cff5f" />

<br/>

# Stage 6 : SonarQube Quality Gates

These are the conditions in Sonarqube. If these conditions are passed then we can say our code is fine -

<img width="1628" height="885" alt="image" src="https://github.com/user-attachments/assets/24bde510-4ac8-429f-ba2b-224ea255cfc2" />


# Create Webhook in SonarQube.

<br/>
Check Credentials >> SonarQube >> Webhook.md

<br/>

<img width="1917" height="291" alt="image" src="https://github.com/user-attachments/assets/fe106ebf-1a42-4b10-820d-caf7d3338867" />


<br/>

# Stage 7 : Build


<img width="1888" height="191" alt="image" src="https://github.com/user-attachments/assets/c9d1cda3-75e0-4125-91df-22316f1f0e0b" />

<br/>

# Stage 8 : Publish to Nexus
<br/><br/>
In order to publish artifact to Nexus repository, we have to follow below steps -<br/><br/>
Add to JavaApplication's POM.xml file under section >> distributionManagement >> repository >> URL<br/>
Go to Nexus >> Nexus repository >> maven-released >> URL >> Copy<br/><br/>
Paste in POM.xml inside URL<br/><br/>
<br/>
<img width="1764" height="407" alt="image" src="https://github.com/user-attachments/assets/2056e376-9963-4c13-ab62-0360145d89be" />

<br/>
Add to JavaApplication's POM.xml file under section >> distributionManagement >> snapshotRepository >> URL<br/>
Go to Nexus >> Nexus repository >> maven-snapshot >> URL >> Copy<br/>
Paste in POM.xml inside URL<br/>
<img width="1357" height="388" alt="image" src="https://github.com/user-attachments/assets/28a7012e-9b37-49e1-a0a7-015e945d0d5b" />

<br/>
Do above 2 changes in POM.xml file.
<br/>
<br/>
Add credential to access this repository -
<br/>
<img width="1295" height="460" alt="image" src="https://github.com/user-attachments/assets/4f537944-1f3b-48e7-9b15-d4f03e27d0e5" />

<br/>
Go to Manage Jenkins >> Manage Files >> New Configuration -
<br/>
<img width="861" height="834" alt="image" src="https://github.com/user-attachments/assets/d187b247-a2aa-4c07-a453-f32551616143" />
<img width="765" height="193" alt="image" src="https://github.com/user-attachments/assets/198da1da-2c18-4119-a7f4-1a7d39fb6e16" />

<br/>
Now in Settings.xml file we will provide credentials for accessing Nexus -
<br/><br/>
<img width="1852" height="889" alt="image" src="https://github.com/user-attachments/assets/f8db0425-3edd-40b5-a9a5-7807ec54a20f" />

<br/>
<img width="1272" height="563" alt="image" src="https://github.com/user-attachments/assets/be5ee62a-8dea-49d3-b612-3c8aba647ace" />

<br/>
Look for servers segment and add below 2 segments there & submit - 
<br/>
&lt;server&gt;<br/>
      &lt;id&gt;maven-releases&lt;/id&gt;<br/>
      &lt;username&gt;admin&lt;/username&gt;<br/>
      &lt;password&gt;admin123&lt;/password&gt;<br/>
    &lt;/server&gt;<br/>
<br/>
    &lt;server&gt;<br/>
      &lt;id&gt;maven-snapshots&lt;/id&gt;<br/>
      &lt;username&gt;admin&lt;/username&gt;<br/>
      &lt;password&gt;admin123&lt;/password&gt;<br/>
    &lt;/server&gt;<br/>
<br/>

SAVE.
<br/><br/>
Now go to Pipeline Syntax for publish to nexus - 

<img width="1298" height="598" alt="image" src="https://github.com/user-attachments/assets/8b190f77-f2b6-4ac3-bc6e-2aae85862005" />
<img width="1023" height="128" alt="image" src="https://github.com/user-attachments/assets/c32b88d1-275d-4bdc-b685-98682eb1b62b" />
<img width="1006" height="187" alt="image" src="https://github.com/user-attachments/assets/443a5917-5d57-4816-97d1-5bd60a997c0b" />

Paste the generate code to pipeline -

<img width="1786" height="226" alt="image" src="https://github.com/user-attachments/assets/4d57c48b-2c2b-4454-956f-258083527cd4" />
<br/><br/>

# Stage 9 : Build & Tag Docker Image

Lets take help from Pipeline syntax -

<br/><br/>
If you are using public DockerHub repo, dont provide URL but if you are using private Dockerhub repo like in organization, provide the URL -<br/><br/>
<img width="1333" height="467" alt="image" src="https://github.com/user-attachments/assets/3853c71f-7156-4d73-92e9-53c265a6d1a4" />

<br/><br/>
To add credential, click on Add -
<br/><br/>
<img width="1018" height="552" alt="image" src="https://github.com/user-attachments/assets/b88b9abc-6315-4111-829f-83844662bf24" />

<br/>
Provide userName, Password & Id = Docker-Cred
<br/><br/>
<img width="1840" height="750" alt="image" src="https://github.com/user-attachments/assets/e65fd5c6-9b0d-4e99-a453-82167eef20f0" />

<br/><br/>
<img width="1450" height="278" alt="image" src="https://github.com/user-attachments/assets/1379349a-df10-4af0-969e-3d24c34067b9" />

<br/><br/>

# Stage 10: Docker Image Scan

<br/>
<img width="1553" height="189" alt="image" src="https://github.com/user-attachments/assets/366ddc1d-1d7e-4f7e-aeb3-f5f43a680ac1" />


<br/><br/>

# Stage 11: Push Docker Image

<br/>
<img width="1585" height="266" alt="image" src="https://github.com/user-attachments/assets/179c7c23-3864-466e-af5d-bfc874878d72" />


<br/>
<br/>

<br/>

# For EKS, create service account in Master node

Check EKS-Setup.md

<br/>

Create namespace -<br/>

```bash
kubectl create ns webapps
```

<br/>

Create Service Account yaml file -<br/>
vi ServiceAccount.yaml
paste below code

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: jenkins
  namespace: webapps
```

Create Service account -

 ```bash
kubectl apply -f ServiceAccount.yaml
```

<br/>

<br/>

Create Role yaml file -

<br/>
vi Role.yaml
paste below code

<br/>

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: app-role
  namespace: webapps
rules:
  - apiGroups:
        - ""
        - apps
        - autoscaling
        - batch
        - extensions
        - policy
        - rbac.authorization.k8s.io
    resources:
      - pods
      - secrets
      - componentstatuses
      - configmaps
      - daemonsets
      - deployments
      - events
      - endpoints
      - horizontalpodautoscalers
      - ingress
      - jobs
      - limitranges
      - namespaces
      - nodes
      - pods
      - persistentvolumes
      - persistentvolumeclaims
      - resourcequotas
      - replicasets
      - replicationcontrollers
      - serviceaccounts
      - services
    verbs: ["get", "list", "watch", "create", "update", "patch", "delete"]
```


<br/>

<br/>

Create Role -

Create Service account -

 ```bash
kubectl apply -f Role.yaml
```

<br/>

<br/>

Bind Role to Service Account -

<br/>
vi BindRole.yaml
<br/>

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: app-rolebinding
  namespace: webapps 
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: Role
  name: app-role 
subjects:
- namespace: webapps 
  kind: ServiceAccount
  name: jenkins 
```

<br/>

<br/>

 ```bash
kubectl apply -f BindRole.yaml
```

<br/>

<br/>

Now Jenkins user has permission to deploy application on EKS.

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>






<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

# NEXUS

Copy IP address and place it with port 8081. Get UI of Nexus, id = admin, password=admin123, select disable ananymous access -

<img width="475" height="483" alt="image" src="https://github.com/user-attachments/assets/f3dfba17-5e43-4f54-8339-b9d8cbd34ee8" />

Nexus is accessible to you -

<img width="1105" height="927" alt="image" src="https://github.com/user-attachments/assets/88b7b6bd-5828-4935-9b41-12f59d295e9f" />

