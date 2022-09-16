# Step-by-step installation of Apache-superset on Windows server 2019

**🙋‍♂️ INFO:** If you have fixes/suggestions to for this doc, please comment below.

**🌟 STAR:** This doc if you found this document helpful.

---

1.) Enable WSL(Windows subsystem for Linux) on Windows Server 2019.  
Go to Server Manager>Manage>Add Roles and features>Check the enable windows subsystem for linux.
 ![image1](https://user-images.githubusercontent.com/96629547/190019856-b6d0c160-64a8-4cd8-87f3-ebfe4e432a84.png)
 **or** 
 Run below command 
 ```
 Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
 ```
⭐ Sometimes server takes time to restart. Please wait for it...

2.) Install Linux Distribution on your system  
Follow these steps--> [Run Linux Distro of your choice](https://computingforgeeks.com/run-linux-on-windows-server/).
or 
Run the following command to install the Ubuntu 18.04 distro
```
Invoke-WebRequest -Uri https://aka.ms/wsl-ubuntu-1804 -Outfile Ubuntu.appx -UseBasicParsing
```
![image2](https://user-images.githubusercontent.com/96629547/190021595-d331fa70-3ce4-4d7c-a5df-9a90dd60cfa8.png)
After downloading extract the zip file and run the .exe file to install the Ubuntu 18 as show below.
```
ls
Rename-Item .\Ubuntu.appx Ubuntu.zip
Expand-Archive .\Ubuntu.zip Ubuntu
cd .\Ubuntu\
.\ubuntu1804.exe
```

Now Open the Ubuntu app from search option:

![image3](https://user-images.githubusercontent.com/96629547/190022819-d8b7a1e7-43cb-47fb-b1b8-bc050d8ffdfb.png)

3.) Once you have both up and running, run the following commands in the Linux terminal mentioned here to installing Apache Superset:
First run the following command:  
```
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install -y python3-pip
```
 [Install Apache-superset installation guide](https://superset.apache.org/docs/installation/installing-superset-from-scratch/)

Troubleshooot  
```
pip list
python -m pip install -U pip
```
⭐⭐⭐To solve the error come while running `superset db upgrade`
```
pip install itsdangerous==1.1.0
pip install sqlalchemy==1.3.24
pip install flask-appbuilder==3.1.1
pip install werkzeug==0.16.1
pip install flask-WTF==0.14.2
```
Now Create an admin user in your metadata database and provide credentials: 
```
export FLASK_APP=superset
superset fab create-admin
```
![image4](https://user-images.githubusercontent.com/96629547/190027683-0bf3457f-4705-4769-afc9-ce13e286131e.png)
- Load some data to play with:  
`superset load_examples`
- Create default roles and permissions.  
`superset init`
- Start a development web server on port 8088, use -p to bind to another port.  
`superset run -p 8088 --with-threads --reload --debugger`
If everything worked, you should be able to navigate to hostname:port in your browser (e.g. locally by default at localhost:8088 or  http://127.0.0.1:8088/login/) and login using the username and password you created.






Refrences: 
- https://www.easeus.com/data-recovery/python-setup-py-egg-info-failed-with-error-code-1.html
- https://stackoverflow.com/questions/65193345/installing-apache-superset-on-windows-server-2019-and-connecting-superset-with
