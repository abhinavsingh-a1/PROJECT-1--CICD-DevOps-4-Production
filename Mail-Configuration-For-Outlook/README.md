
```bash
sudo apt update
```


Install Openjdk

```bash
sudo apt install fontconfig openjdk-21-jre
```

Install Jenkins

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```

Now after installation verify that jenkins is running or not. For that what we should do is - <br/>
Copy public ip of EC2 instance.<br/>
For example: 54.144.2.136 is my public IP<br/>
So in browser I will paste -<br/>
http://54.144.2.136:8080/<br/>
8080 is the port where jenkins is running.<br/><br/>

First you will see this, where we have to provide the administration password -
<img width="860" height="594" alt="image" src="https://github.com/user-attachments/assets/a192982e-0f43-4e43-9e4c-ba69fa42e042" />


<img width="1582" height="733" alt="image" src="https://github.com/user-attachments/assets/165d55bd-71bb-4f47-b95c-5ddbbc92f5c9" />

You will get one string, which we have to paste in UI -
<img width="747" height="48" alt="image" src="https://github.com/user-attachments/assets/b84742ff-a7df-42a1-b9a1-f70e47b09a71" />

We will get 2 options -
<img width="754" height="463" alt="image" src="https://github.com/user-attachments/assets/ba96b24e-df6d-49ed-883b-d35d2610c6cb" />

Click on installed suggested plugin, and it will start setting up -
<img width="839" height="546" alt="image" src="https://github.com/user-attachments/assets/c1b59963-a2e3-4d28-bf6d-3b89279abd1b" />

Login to outlook & go to settings >> Forwarding & IMAP >> Pop & IMAP -
Enable both

Go to -
https://account.microsoft.com/

Go to -
Security >> Account Security >> Manage how i sign in

2 Step verification will be off -
<img width="1375" height="514" alt="image" src="https://github.com/user-attachments/assets/c84b7136-40a2-423e-a672-00490bc49b15" />

Click on turn on, select app option & install authenticator app, scan code and account will be added in authenticator app & two step verification will be turn on -
<img width="1198" height="309" alt="image" src="https://github.com/user-attachments/assets/84fb4a88-5987-4e56-9a52-e45f622c2b8e" />

Below you will find app password section, click on create new app password -
copy password & save it somewhere -
<img width="1857" height="184" alt="image" src="https://github.com/user-attachments/assets/7c06f36a-6c53-4776-b659-a9af2f87a389" />



Now go to Jenkins and setup mandatory fields -
<img width="862" height="597" alt="image" src="https://github.com/user-attachments/assets/51406e57-44cf-41b7-b315-a55af72907bf" />


Go to Manage Jenkins >> Plugins >> Installed Plugins -
Search for email
Make sure that email extension plugin should be enabled.

<img width="1886" height="382" alt="image" src="https://github.com/user-attachments/assets/dec20e46-6919-4a60-ad03-55bd0ccc540d" />

Now go to Jenkins >> Manage Jenkins >> System -
Scroll down and you will find section extended email notification.

SMTP Server : smtp.office365.com
Port : 587
Under Port, click on advanced button -
Credentials >> Add >> With Username & password -
Provide all fields -
<img width="538" height="643" alt="image" src="https://github.com/user-attachments/assets/44369ff8-0d06-45ed-a066-f7788cc22b51" />

Password will be app password which we created recently.

Select >> Use TLS 

Default user e-mail suffix : @outlook.com
Reply To List : youroutlookemail@outlook.com

Click on Default trigger button >> Select Always

Now Email notification section will appear.
Set it up as below -
<img width="1606" height="869" alt="image" src="https://github.com/user-attachments/assets/850e3113-272d-4ddc-be4c-2b74328da629" />
Apply




