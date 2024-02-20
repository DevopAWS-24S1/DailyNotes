# Recap of Session-1:
1. Vitual machine Vs Physical machine 
2. Where are the servers are created ..?
        * On-premise 
        * Cloud 
3. On-premise Vs Cloud (AWS , Azure , GCP) 
4. Operating Systems - Windows & Linux 
5. Kinds of Interface for Servers >> 1. GUI 2. CLI 
6. How linux OS works internally ..?
        * CLI >> Kernel >> Hardware >> kernel >> CLI 
7. Linux is not an OS . It is a kernel developed by Linus Torvalds. 
* Ex: - Ubuntu , Redhat , Centos, Amazon linux 2 
8 . Created a Ubuntu server in AWS 



# Decode  AWS connect command 
```
ssh -i "DevopAWS.pem" ubuntu@ec2-35-172-211-1.compute-1.amazonaws.com
ssh username@ipaddress
```
* SSH - Secureshell 
* DevopAWS.pem - Acts as a Password 
* Ubuntu - default user created by AWS 
* ec2-35-172-211-1.compute-1.amazonaws.com - a name give by the AWS for the server instead of ip address 

# Connect to the server :
* Laptop - Username/password 
* Server from your laptop -- username / password / ipaddress
* Defaultgateway - Modemip - 192.168.0.1
* ipv4 address - Private IP -  192.168.0.233
* Public IP - 103.95.173.231
* Till 1995 we have only public ips 

# Kinds of Authentication:
1. PasswordBased - username & password 
2. keybased/ passwordlesss  -- key based files to connect to the server 


# How internet works :
* Amazon.in 
*when you hit Amazon.in in your laptop >> it will contact ISP to get the ip(ISP is responsible for providing IP) >> Modem checks is that ip is in your network/home..? >> modem goes to ISP and check if that ip is there in the BSNL ISP >> BSNL ISP goes to Peering point/Exchange point(It is point wwhere all the networks are connected) >> fibre exchange point in India to connect to the world (Mumbai,chennai,kerala)>> US fibre excahnge point >>ISP >> Modem >> Amazon.in server


# CRUD operations:
* Create, Read, Update, Delete 
* touch filename
* mkdir foldername
* cat filename
* cat -n filename
* rm filename
* rm -rf foldername
* f >> force delete 
* cp SOURCE DESTINATION
* mv SOURCE DESTINAION
* head filename  - print 10 files from first 
* tail filename  - print 10 files from last  
* head -n 5 filename
* tail -n 5 filename
* grep <SearchWord> filename
* grep -i <SearchWord> filename
* wget https://git-scm.com/download/win
* cut awk 
* 2024-02-20 
* find <pathtofind> -name <filename>

# Assignment:
* Look at  how vi editor works in linux 
