# Recap of previous session:
* Ansible is one of the configuration management tool and it is also used for the deployment.
* Playbook - you will define your desired state in the playbook 
* Install tomcat -- desired state 
* Write playbook using yaml syntax 
* YAML - yet another markup language 
* Inventory -- You will define where to run your playbook



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
KbdInteractiveAuthentication yes

```

sudo service sshd restart

```

##  Step-4: Create keys on the Ansible Server & copy the keys from Ansible server to the Ansible Node

```
sudo su devops
ssh-keygen
ssh-copy-id username@publicipaddress    -- usernamee & publicipaddress of ansible node 

```

##  Step-5: Install the Ansible on the Ansible Server 

```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```


```
ansible --version
```

##  Step-6: Install python the Ansible Node

```
python3 -V

```

```
sudo apt-get update
sudo apt-get install python3

```

# Inventory :
* Default Inventory file   --  /etc/ansible/hosts
* Customised Inventory file   -- /pathofyourchoice/


# Check the ansible connectivity:
* use below command with the Publicip of ansible node placed in the /etc/ansible/hosts

```
ansible -m ping all
ansible -i /home/devops/hosts -m ping all
```


## Deployment process organizations follow:
* In lower environments like DEV, QA, PRE-PROD -- No need of approvals from CLIENTS/MANAGERS 
* When you try to deploy it on PROD/LIVE -- CAB process 
* CHANGE ANALYSIS BOARD 
* CAB ticket -- JIRA ticket 

1. Normal 
2. Expedite 
3. Emergency 
