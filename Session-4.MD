# 2. PackageManagement
* Ubuntu - apt 
* Centos - yum 

```
apt install git 
apt install nginx -y 
```
* Nginx is popular web server for the frontend
* Bydefault ubuntu servers will have the git installed 
* To check the git version
```
git --version
```


* While installing softwares or run application in your server ,  there a process created for that s/w or application and it runs as a service.

* apt list --installed >> list the installed packages 
* apt list >> all packages along with installed 
* apt search openjdk-11-jdk > to search the package 
* apt remove nginx >> uninstall package 

# ProcessManagement & ServiceManagement
* While installing softwares or run application in your server ,  there a process created for that s/w or application and it runs as a service.
* ps -ef >> list all processes running in the server 
* ps -ef | grep ssh 
* pid and ppid 
* Processid & ParentProcessId
* kill pid  >> kill the process
* kill -9 pid >> force kill
* top 
* q - to comeout of the top command 
* stop/tart/restarting/status
* sudo service nginx start/stop/restart/status
* sudo service nginx status 
* sudo service nginx start 
* sudo service nginx stop
* sudo service nginx restart 

* sudo systemctl enable nginx  
* sudo systemctl stop nginx 


* Every service runs on a port in the server
* nginx - 80 - http
* ssh - 22
* tomcat - 8080
* https - 443
* 0 - 65535 ports


#  Security groups in aws / Firewall :
1. Inbound Rule >> traffic comes inside to the server 
2. Outboud Rule >> traffic going outside from the server 
3. 0.0.0.0/0 - Anyone can access your server through ssh . If they have usernamee/passwd or Keybasedauthetiction
* All Traffic - open all ports 

# NetworkManagement 
* netstat -l 
* ping publicipaddrss >> checks basic connection
* telnet publicip <portnumer>
* telnet <google.com> 443
* df -h
* free -m 
* free - h


# Monolithic vs Microservices:
* App are very big , because they are going to develop the frontend the backend as a single code .
* A simple change need to be deployed again for the wholw application
* Maintanance is very difficult - single point of failure 
* Stick to single deveoplement language - compatability 
* .ear > enterprize archive 


# Three Tier Application 
* Webtier - Frontend 
* App tier -- backend 
* DB tier - Database 
* When some small change in webtier , whole wetier has to be deployed again 
* communication happens on API calls from frontend to backed 


# Microservices :
* Containers - use the resouces at the fullest level 
* scale easily 
* Monitor easily 
