# Recap 
1. Key-value pairs 
2. List 
3. Dictionaries 
4. Nested Structures

* Sample ansible playbook syntax.
* Playbook to install java 
* Run the playbook 
* Check the syntax of playbook 
* Dry-run 

# Tomcat :
* Tomcat is an application server 

# Playbook for install tomcat and restart:

```
sudo apt-get update 
sudo apt-get install openjdk-11-jdk


sudo apt-get update 
sudo apt-get install tomcat9 

sudo service tomcat9 restart 
```

```
---
- hosts: all
  become: yes
  tasks:
    - name: Install Java
      apt:
        name: openjdk-11-jdk
        state: present 
        update_cache: yes
    - name: Install Tomcat9
      apt:
        name: tomcat9
        state: present
        update_cache: yes
    - name: Restart tomcat9
      service:
        name: tomcat9
        state: restarted
        enabled: yes
          
```

* Check syntax:

```
ansible-playbook -i /home/devops/hosts tomcat.yml --syntax-check
```


# Create two more servers and add them as a Ansible node. To visualize Three tier setup.
1. Create User , Give sudo access 
2. Make password Authentication enabled , restart sshd service 
3. Copy the keys from Ansible Server to the nelwy created servers
4. Add the new server ips to the /home/devopss/hosts
```
ansible -i /home/devopss/hosts -m ping all
```
1. AppServer  - Tomcat 
2. WebServer  - Apache is webserver
3. DBServer   - SQL / NOSQL 


* cat hosts 

```
3.91.201.3
3.91.175.40
34.201.60.167
```


```
[all]

[webservers]
34.201.60.167



[appserver]
3.91.201.3

[dbserver]
3.91.175.40

```


```
---
- hosts: appserver
  become: yes
  tasks:
    - name: Install Java
      apt:
        name: openjdk-11-jdk
        state: present 
        update_cache: yes
    - name: Install Tomcat9
      apt:
        name: tomcat9
        state: present
        update_cache: yes
    - name: Restart tomcat9
      service:
        name: tomcat9
        state: restarted
        enabled: yes
          
```

* -b    >> it is used to specify the section from the host file 
```
ansible -i hosts -m ping -b appserver
```
* Run the above playbook 
```
ansible-playbook -i /home/devops/hosts tomcat.yml

```


# Adhoc commands in ansible :
* Adhoc commands are also going to give you the same output like the playbook. 
* You can use only on module at at time in adhoc commands 
* Adhoc Commands Document: https://docs.ansible.com/ansible/latest/command_guide/intro_adhoc.html

* Syntax:

```
ansible [pattern] -m [module] -a "[module options]"

```

```
ansible -i hosts -m ping all
```

# Variables in Ansible :

* Syntax:
```
"{ package_name }"
```

* DRY and also for reusing your scripts 
* You can define the value to a variable in four areas in Ansible 
1. Host level
2. Group level
3. Playbook level 
4. Command line level


* cat hosts :

```
[all]

[webservers]
34.201.60.167 



[appserver]
3.91.201.3 package_name=tomcat9  # This is defining at host level 
3.91.201.4

# This is defining at group level 
[appserver]
package_name=tomcat9

[dbserver]
3.91.175.40

```


* java.yml 

```
---
- hosts: appserver
  become: yes
  tasks:
    - name : Install software 
      apt:
        name: "{ package_name }"
        state: present
        update_cache: yes
```

* Defining varaiable value at playbook level 


```
---
- hosts: appserver
  become: yes
  vars:
    package_name:
      - tomcat9
  tasks:
    - name : Install software 
      apt:
        name: "{ package_name }"
        state: present
        update_cache: yes
```

* Defining varaiable value at commandline level 
```
ansible-playbook -i /home/devops/hosts -e "package_name=tomcat9" java.yml
```

