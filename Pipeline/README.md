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
<br/>
Add tools & first stage Git Checkout -
<br/>
<img width="1302" height="617" alt="image" src="https://github.com/user-attachments/assets/32766e60-bb2e-4900-99f2-14a8f2df1fb7" />

<br/>Use Pipeline syntex to create snippet.
<br/>Select git, paste repo URL, And add credentials with username & password -
<br/>
<img width="1531" height="788" alt="image" src="https://github.com/user-attachments/assets/7ffc6b40-c792-4bab-ad57-fced2f73354e" />

<br/>Click on generate pipeline script -

<br/><img width="1319" height="716" alt="image" src="https://github.com/user-attachments/assets/7d6770de-c481-4a59-96dd-9eaa42875e5d" />

<br/>Copy syntax and paste in pipeline under steps.
<br/><br/><br/>

# Generate SonarQube Token. 
## Check credentials >> Sonarqube >> README.md<br/>


# Add Sonarqube token as secret text credential in Jenkins<br/>
## Check Credential >> Jenkins >> README.md

<br/>
Lets go back to pipeline syntax -
<br/>
<img width="1322" height="521" alt="image" src="https://github.com/user-attachments/assets/782a5b3a-5c65-491e-9cd3-c866ef47fd48" />

<br/>
Paste syntax in pipeline -
<br/>
<img width="1234" height="528" alt="image" src="https://github.com/user-attachments/assets/079a7fbe-eae9-41b9-837b-ca2b060cff5f" />

<br/>

# Create Webhook in SonarQube.

<br/>
Check Credentials >> SonarQube >> Webhook.md

<br/><br/><br/>


Add to JavaApplication's POM.xml file under section >> distributionManagement >> repository >> URL<br/>
Go to Nexus >> Nexus repository >> maven-released >> URL >> Copy<br/>
Paste in POM.xml inside URL<br/>
<br/>
<img width="1764" height="407" alt="image" src="https://github.com/user-attachments/assets/2056e376-9963-4c13-ab62-0360145d89be" />

<br/>
Add to JavaApplication's POM.xml file under section >> distributionManagement >> snapshotRepository >> URL<br/>
Go to Nexus >> Nexus repository >> maven-snapshot >> URL >> Copy<br/>
Paste in POM.xml inside URL<br/>
<br/>
Do above 2 changes in POM.xml file.
<br/>
<br/>
Go to Manage Jenkins >> Manage Files >> New Configuration -
<br/>
<img width="861" height="834" alt="image" src="https://github.com/user-attachments/assets/d187b247-a2aa-4c07-a453-f32551616143" />
<img width="765" height="193" alt="image" src="https://github.com/user-attachments/assets/198da1da-2c18-4119-a7f4-1a7d39fb6e16" />

<br/>
Now in Settings.xml file we will provide credentials for accessing Nexus -
<br/><br/><br/><br/>
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
<br/>
# For EKS, create service account (Follow EKS-Setup.md document) -
<br/>
Create namespace -<br/>
```bash
kubectl create ns webapps
```
<br/>
Create Service Account -<br/>
```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: jenkins
  namespace: webapps
```
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

