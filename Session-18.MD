# Recap 
* Groups in hosts file 
* Plabook for installing Tomcat
* Tomcat is an application server 
* variables in ansible 
    * How to write a variable ..?
    * How to pass the value to the variable ..?
        1. Hosts level 
        2. Group level 
        3. Playbook level 
        4. Commandline level 

* Variable syntax:

```
"{ varibale_name }"
```


# Playbook to install software 

```
---
- hosts: appservers
  become: yes 
  tasks:
    - name: Install Software
      apt:
        name: "{{ package_name }}"
        state: present
        update_cache: yes
```



* host 

```
[all]

[webservers]
34.201.41.73


[appservers]
52.90.223.10 package_name=openjdk-11-jdk # Assigning value at host level 

[appservers:vars]
package_name=openjdk-11-jdk # Assigning value at group  level 

[dbservers]
3.82.151.150

```

* Playbook level assigning vlaue to a variable 
```
---
- hosts: appservers
  become: yes 
  vars:
    package_name:
      - tomcat9
  tasks:
    - name: Install Software
      apt:
        name: "{ package_name }"
        state: present
        update_cache: yes
```


* Assigning value at command line level:

```
ansible-playbook -i /home/devops/hosts variable.yml -e "package_name=openjdk-11-jdk"
```




# Practice Host level variable by using below ost file and playbook

* hosts

```
[all]

[webservers]
34.201.41.73


[appservers]
52.90.223.10 package_name=openjdk-11-jdk # Assigning value at host level 

[dbservers]
3.82.151.150

```

* playbook 

```
---
- hosts: appservers
  become: yes 
  tasks:
    - name: Install Software
      apt:
        name: "{{ package_name }}"
        state: present
        update_cache: yes
```


# Practice Group level vraible by using below hsts file and playbook file:
 

* hosts 

```
[all]

[webservers]
34.201.41.73


[appservers]
52.90.223.10 

[appservers:vars]
package_name=openjdk-11-jdk


[dbservers]
3.82.151.150
```
* Playbook 

```
---
- hosts: appservers
  become: yes 
  tasks:
    - name: Install Software
      apt:
        name: "{{ package_name }}"
        state: present
        update_cache: yes
```

# Practice the playbook level variable by using below hosts and plabok file :


* hosts 

```
[all]

[webservers]
34.201.41.73


[appservers]
52.90.223.10 



[dbservers]
3.82.151.150
```

* playbook 


```
---
- hosts: appservers
  become: yes 
  vars: 
    package_name:
      - openjdk-11-jdk
  tasks:
    - name: Install Software
      apt:
        name: "{{ package_name }}"
        state: present
        update_cache: yes
```


# Practie assigning value at command line levl by using below hosts and playbook file :

* hosts 

```
[all]

[webservers]
34.201.41.73


[appservers]
52.90.223.10 



[dbservers]
3.82.151.150

```

* playbook 


```
---
- hosts: appservers
  become: yes 
  tasks:
    - name: Install Software
      apt:
        name: "{{ package_name }}"
        state: present
        update_cache: yes
```

* playbook level variable

```
ansible-playbook -i hosts -e "package_name=openjdk-11-jdk" varaible.yml
```

# Exercise :
* Try to provide value of a variable in all four areas (hostlevel, group level, playbook level & command line level )
* openjdk-11-jdk , maven , tree , tomcat9 


# Conditions & Loops in Ansible :

* Loops help us in running the same task with multiple values

# Plabook to install  java , tomcat using loops 

* Loops Documentation: https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_loops.html

* Playbook 

```
---
- hosts: appservers
  become: yes 
  tasks:
    - name: Install Software
      apt:
        name: "{{ item }}"
        state: present
        update_cache: yes
      loop:
        - openjdk-11-jdk
        - tomcat9
```

* hosts 
```
[all]

[webservers]
34.201.41.73


[appservers]
52.90.223.10 



[dbservers]
3.82.151.150

```

# Conditions:
* AnsibleFacts Documentation: https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_vars_facts.html
* Ansible_facts : While playbook is running , in the step of gathering facts , the informatiin about the remote servers(ansible Node) are gathered and stored in the form of variables 

* Centos OS >> Redhat
* Ubuntu OS  >> Debian

```
ansible['os_family]' == "Debian"

```

# Playbook to install java both on centos and ubuntu 

* hosts 
```
[all]

[webservers]
34.201.41.73


[appservers]
52.90.223.10 



[dbservers]
3.82.151.150

```

* Playbook 

```
---
- hosts: appservers
  become: yes 
  tasks:
    - name: Install java on ubuntu 
      apt:
        name: openjdk-11-jdk
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "Debian"
    - name: Install java on Centos 
      yum :
        name: openjdk-11-jdk
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "RedHat"

```


# Package module 
* It is going to helps us in installing both the Debian and Redhat packages


```
---
- hosts: appservers
  become: yes 
  tasks:
    - name: Install java on ubuntu 
      package:
        name: openjdk-11-jdk
        state: present
        update_cache: yes
      
```

* Apcahe is weberver 
* Install Apache in ubuntu 

```
sudo apt-get install apache2
```

* Install Apache in Redhat 

```
sudo yum install httpd
```

* Playbook : 

```
---
- hosts: appservers
  become: yes 
  tasks:
    - name: Install apache2 on ubuntu 
      package:
        name: apache2
        state: present
        update_cache: yes
    - name: Install apache2 on Centos
      package:
        name: httpd
        state: present
        update_cache: yes
      
```