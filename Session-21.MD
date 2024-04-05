# include and import :
* Import & Include documentation : - https://docs.ansible.com/ansible/2.9/user_guide/playbooks_reuse_includes.html#id1

* syntax:

```
- import_playbook: java.yml
```


* java.yml

```
- hosts: all
  become: yes
  tasks: 
    - name: Install java
      apt:
        name: openjdk-11-jdk
        state: present
        update_cache: yes
```

* Install tomcat 
    * The prerequesite is java
    * write a playbook to install java and tomcat 

* tomcat.yml
```
---
- import_playbook: java.yml
- hosts: all
  become: yes
  tasks: 
    - name: Install tomcat 
      apt:
        name: tomcat9
        state: present 
        update_cache: yes 
    - name: Restart Tomcat 
      service:
        name: tomcat9
        state: restarted

```


# Include:

* includejava.yml

```
- name: Install java
  apt: 
    name: openjdk-11-jdk
    state: present
    update_cache: yes

```

* includetomcat.yml

```
---
- hosts: all
  become: yes
  tasks: 
    - include_tasks: includejava.yml
    - name: Install tomcat 
      apt:
        name: tomcat9
        state: present 
        update_cache: yes 
    - name: Restart Tomcat 
      service:
        name: tomcat9
        state: restarted

```

# Deploy Static Website on Apache :
* Static website content is not going to be changees untill changes made by the developer to the code.
* Typically statuc websites are written in HTML , CSS , Jvascripting(JS)
* Also the Static webiste written in html , css and js doesn't require building the code 

## Manual steps to deploy static website :
1. CodeRepo written by the developer - https://github.com/DevopAWS-24S1/Tour-Project.git
2. Take a server from AWS and install apache on it 
3. git clone https://github.com/DevopAWS-24S1/Tour-Project.git  to the path /var/www/html/  to the Webserver
4. Restart the apache on the webserver 

* Humans can remember only names not the ip's 
* DNS - Domain naming system 
* DNS Providers :
  * Godady 
  * Amazon
  * Azure
  * Hostinger 

* Buy a domain in Hostinger for practice stuff. (Buy a cheaper domain)
