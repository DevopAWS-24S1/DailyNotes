# Practice of last previous sesions:
* Loops  -- In install multiple softwares , loop the values to a singe task 
* Conditions -- We can put conditions to the task . Ex :  run only when os is belongs to Debian 
* Fail module -- It is going print the message when something is failing
* Handler -- You create handler and call the handler at any point of playbook when you need it 


# Centos Node setup 
* Create a server from AWS . Take centOS 8 as Operating System
* Configure the Centos Node to the ansible server
    1. Create a user devops and provide sudo access 
    ```
    adduser devops
    passwd devops
    visudo
    ```
    2. Make the PasswordAuthentication enabled for the server 
    ```
    vi /etc/ssh/sshd_config

    sudo service sshd restart 
    ```
    3. Copy the keys from Ansible server to the Ansible node(CentOS server)
    ```
    sudo su - devops 
    ssh-copy-id devops@centosPublicip
    ```


# Playbook to install apache in Ubuntu OS :

*  hosts

```
[all]

[webservers]
54.173.239.94
54.173.239.74 


```

* Playbook 

```
---
- hosts: webservers
  become: yes
  tasks:
    - name: Install Apache on Ubuntu 
      apt:
        name: apache2
        state: present
        update_cache: yes
```

* Conditions :

* This playbook is going to check the OS , if OS is Debian it is going to install Apache. If not it will fail 
```
---
- hosts: Webserver
  become: yes
  tasks:
    - name: Install Apache on Ubuntu 
      apt:
        name: apache2
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "Debian"
```


# Playbook to install apache in CentOS :

*  hosts

```
[all]

[webservers]
54.173.239.94
54.173.239.74 


```

* Playbook 

```
---
- hosts: webservers
  become: yes
  tasks:
    - name: Install Apache on Ubuntu 
      yum:
        name: httpd
        state: present
        update_cache: yes
```

* Conditions :
* This playbook is going to check the OS , if OS is CentOS it is going to install Apache. If not it will fail 
```
---
- hosts: Webserver
  become: yes
  tasks:
    - name: Install Apache on Ubuntu 
      yum:
        name: httpd
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "RedHat"
```

# Single playbook to install Apache on both ubuntu and Centos :


*  hosts

```
[all]

[webservers]
54.173.239.94 - Ubuntu 
54.173.239.74 - centos


```

* Playbook 

```
---
- hosts: webservers
  become: yes
  tasks:
    - name: Install Apache on Centoa 
      yum:
        name: httpd
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "RedHat"
    - name: Install Apache on Ubuntu 
      apt:
        name: apache2
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "Debian"
    
```

* package 

```
---
- hosts: webservers
  become: yes
  tasks:
    - name : Install Apache on Ubuntu
      package:
        name: apache2
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "Debian"
    - name: Install Apache on Centos 
      package:
        name: httpd
        state: present 
        update_cache: yes 
      when: ansible_facts['os_family'] == "RedHat"

```


# Handler 

* hosts 
```
54.173.239.94
```

* playbook 

```
---
- hosts: webservers
  become: yes
  tasks:
    - name: installing apache2
      apt:
        name: apache2
        state: present
        update_cache: yes
      notify:
      - restart apache2
  handlers:
    - name: restart apache2 
      service:
        name: apache2
        enabled: yes 
        state: restarted
```