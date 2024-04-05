# Recap 
* Deployed the Static tour website .
* Bought a domain from hostinger - tourtest.site

# Steps to be followed for Deploying using Ansible Playbook:
1. Clone the code 
2. Write a playbook to install apache , copy the code , restart the apache2 server 
* copy Module : https://docs.ansible.com/ansible/2.9/modules/copy_module.html#copy-module   
3. Rollback mechanism :
   * Taking backup of existing code - backup of html folder 


```
- hosts: all
  become: yes 
  tasks:
    - name: Install apache
      apt:
        name: apache2
        state: present
        update_cache: yes
    - name: Backup of html folder
      archive:
        path: /var/www/html
        dest: /var/www/html.tar.gz
        format: gz
    - name: Copy the code 
      copy:
        src: /home/devops/Tour-Project/
        dest: /var/www/html/
    - name: Restart Apache
      service:
        name: apache2
        state: restarted
      
```

# Deployment on the AppServer
* Below are the requirements:

1. CodeRepo
```
git clone https://github.com/DevopAWS-24S1/Java-Hello-World.git
```
2. Build the code 
```
mvn package
```
4. Write  Ansible playbook to deploy the code to the Appserver
   * Task to install java , tomcat 
   * Backup - archive module 
   * Copy the code - copy module
   ```
   src: /home/devops/AppserverDeployment/Java-Hello-World/target/Devops-Surya-1.0.0.jar
   dest: /var/lib/tomcat9/webapps/
   ```
   * Restart the tomcat 


```
- hosts: all
  become: yes
  tasks:
    - name: Install java 
      apt: 
        name: openjdk-11-jdk
        state: present
        update_cache: yes
    - name: Install Tomcat9
      apt: 
        name: tomcat9
        state: present
        update_cache: yes
    - name: copy the code 
      copy:
        src: /home/devops/AppserverDeployment/Java-Hello-World/target/Devops-Surya-1.0.0.jar
        dest: /var/lib/tomcat9/webapps/
    - name: Restart tomcat 
      service:
        name: tomcat9 
        state: restarted

```

* Rollback Mechanism 

```
- hosts: all
  become: yes
  tasks:
    - name: Install java 
      apt: 
        name: openjdk-11-jdk
        state: present
        update_cache: yes
    - name: Install Tomcat9
      apt: 
        name: tomcat9
        state: present
        update_cache: yes
    - name: Backup of existing code
      archive:
        path: /var/lib/tomcat9/webapps/Devops-Surya-1.0.0.jar
        dest: /var/lib/tomcat9/webapps/Devops-Surya-1.0.0.jar.tar.gz
        format: gz
    - name: copy the code 
      copy:
        src: /home/devops/AppserverDeployment/Java-Hello-World/target/Devops-Surya-1.0.0.jar
        dest: /var/lib/tomcat9/webapps/
    - name: Restart tomcat 
      service:
        name: tomcat9 
        state: restarted

```


# Shell & Comand  Modules :
* These modules helps us in running the linux command directly 

* Shell

```
- name: Execute the command in remote shell; stdout goes to the specified file on the remote.
  shell: sudo apt-get install apache2
```

* Command 

```
- name: Run command if /path/to/database does not exist (without 'args' keyword).
  command: /usr/bin/make_database.sh db_user db_name creates=/path/to/database
```


