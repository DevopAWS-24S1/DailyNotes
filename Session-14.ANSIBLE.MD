# Ansible :

## Recap of Basic Devops Pipeline :

* Ansible is one of the configuration management tool and also it is used for deploying the code .
* Configuration Management(CM) : Application requires sotwares to be installed and configured . The procees of doing the installation and configurations is called as CM 
* Ansible is a Push type of CM 

# Push vs Pull 
* In push type , desires state will be pushed to the VMS from AnsibleServer.
* In pull type. VM's will pull the desired state from the ChefServer.

* ```Desired State```: Whatevver you wanted to do using ansible is called as desired state.
* Ex: Install tomcat is your desired state 

* ```playbook```: We will define our desired state , by using yaml syntaxin the playbook

* ```Inventory```: In inventory , you will define where to run the playbook (on which server you want run the playbook)


# Create Ansible setup :
##  Step-1: Create user on the Ansible server & provide sudo access 

```
sudo su - 
adduser devops
```

* visudo 

```
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
%devops ALL=(ALL:ALL) NOPASSWD:ALL

```

##  Step-2: Create user on the Ansible Node & provide sudo access

```
sudo su - 
adduser devops
```

* visudo 

```
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
%devops ALL=(ALL:ALL) NOPASSWD:ALL

```

##  Step-3: Password Authentication enabled on both the Ansible server & Ansible server 

```
vi /etc/ssh/sshd_config

* loook for 
```
PasswordAuthentication yes

```

sudo service sshd restart

```

##  Step-4: Create keys on the Ansible Server & copy the keys from Ansible server to the Ansible Node

```
sudo su devops
ssh-keygen
ssh-copy-id username@ipaddress    -- usernamee & ipaddress of ansible node 

```

##  Step-5: Install the Ansible on the Ansible Server 

```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo add-apt-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

##  Step-6: Install python the Ansible Node

```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo add-apt-repository --yes --update ppa:ansible/ansible
$ sudo apt install python

```
