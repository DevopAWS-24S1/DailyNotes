# Playbook to install apache2 in the both CentOS and Debian flavors:
* To install apache2 on centos :

```
yum install httpd 
```

* To install apache2 on ubuntu :

```
apt install apache2 
```

```
---
- hosts: all
  become: yes 
  tasks:
    - name: Installing Apache2 on Debian flavour
      apt:
        name: apache2
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "Debian"
    - name: Instaling Apachee2 on RedHat flavour
      yum:
        name: httpd
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "RedHat"
```

# Package module to install apache2 in both CentOS and Debian flavors:

```
---
- hosts: all
  become: yes
  tasks:
    - name: Installing Apache on Debian flavour 
      package:
        name: apache2
        state: present 
    - name: Installing apache on Redhat Flavour 
      package:
        name: httpd
        state: present
```


# Fail module in ansible 


```
---
- hosts: all
  become: yes
  tasks:
    - name: fail if the os is other than the debian
      fail:
        msg: the playbook run only for the debian os
      when: ansible_facts['os_family'] != "Debian"
    - name: installing apache2
      apt:
        name: apache2
        state: present
        update_cache: yes
      when: ansible_facts['os_family'] == "Debian"
      
```


# Handler : 
* It is similar to the function we practiced in the shell script 
* Function calling >> Write a function >> We call the funtion whenever it is needed
* Using same task multiple times in your playbook , you can write a handler and call the handler when ever you need it .

```
---
- hosts: all
  become: yes 
  tasks:
  handlers:
    - name: Restart apache2
      service:
        name: apache2
        state: restarted
    - name: Calling handler
      notify: 
        - Restart apache2
```



```
---
- hosts: all
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
# Static Websites & Dynamic Websites 
## Static Websites:
* Ex: - Personal blogs , Tour package sites 
* Static websites contains the fixed content that doesnot change untill manually updated by the developer 
* Typically these are developed in HTML , CSS, Java scripting
* Very easy to create and handle


## Dynamic Websites:
* Ex: Amazon , flipkart , e-commerce sites 
* Dynamic websites generate content based on the user interactions , database or other external data sources 
* Three tier  applications >> Web Tier >> App Tier >> DB Tier 
* Little hard to create and hande