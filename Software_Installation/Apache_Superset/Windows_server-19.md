To install Apache-superset on Windows server 2019

1.) Enable Linux on Windows Server 2019.  
 ![image1](https://user-images.githubusercontent.com/96629547/190019856-b6d0c160-64a8-4cd8-87f3-ebfe4e432a84.png)
⭐ Sometimes server takes time to restart. Please wait for it...

2.) Now install WSL on your system-  
Follow these steps--> [Install WSL in Windows server](https://docs.microsoft.com/en-us/windows/wsl/install-on-server). Run this command 
```
Invoke-WebRequest -Uri https://aka.ms/wsl-ubuntu-1804 -Outfile Ubuntu.appx -UseBasicParsing
```
![image2](https://user-images.githubusercontent.com/96629547/190021595-d331fa70-3ce4-4d7c-a5df-9a90dd60cfa8.png)

![image3](https://user-images.githubusercontent.com/96629547/190022819-d8b7a1e7-43cb-47fb-b1b8-bc050d8ffdfb.png)

3.) Once you have both up and running, run the following commands in the Linux terminal mentioned here to installing Apache Superset:
First run the following command:  
```
sudo add-apt-repository universe
sudo apt-get update`
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
