
On top right, click on Account number and select security credentials -

<img width="421" height="745" alt="image" src="https://github.com/user-attachments/assets/2b61a2f1-da74-4022-84e4-ae8d443c9a57" />

Click on Create Access Key -

<img width="1585" height="275" alt="image" src="https://github.com/user-attachments/assets/3213bbaf-5326-4925-9290-29274cbc2e8f" />

<img width="1117" height="513" alt="image" src="https://github.com/user-attachments/assets/bd43c6a3-07fa-4efe-bece-df56cf24a928" />

Go to below URL -

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

As I am on Windows I will install MSI Installer - All Users.

<img width="497" height="386" alt="image" src="https://github.com/user-attachments/assets/93fac75b-05c2-418e-a29b-cb7d4f44054a" />

Open command prompt in admin mode and provide command -

```bash
aws configure
```

<img width="1097" height="195" alt="image" src="https://github.com/user-attachments/assets/d3834a09-1b66-49b2-98fb-8ede2352bca9" />

Provide the access key ID
Secret access key

Now provide below query -

```bash
aws account get-account-information
```

It will give you output of account id, account name, account creation date & account status.

This shows that AWS account is connected correctly.






