# Recap :

* Created a Ansible setup 
* Ansible ping connectivity b/w Ansible server and Ansible Node
* Use Yaml syntax to write a playbook.


# Yaml Syntax Basics:
1. Key-valuepairs
2. Lists
3. Dictionaries
4. Nested Strcutures - (Complex data) 
5. Comment 


1. Key-valuepairs :


* syntax:

```
key: value
```

* Example :

```
name: Surya
age: 30 
Occupation: employee
```

* Above example ```name``` is the kay and ```Surya``` is the value 


2. Lists

* syntax:

```
key:
  - value1
  - value2
```

* Example :

```
fruits:
  - apple
  - mango 
  - banana
```

* In above example key is a ```fruits```, valuers are apple, mango & banana 


3. Dictionaries

* syntax:

```
key:
  key1: value1
  key2: value2
```

* Example :


```
Employee:
  name: Surya
  Designation: Sr Artchitect
```
* In above example ```Employee``` is a key and ``name: surya``` is a key-vale pair 



4. Nested Strcutures 

* Syntax:

```
Key:
  - key1: value1
    key2: value2
  - key3: value3
    key4: vakue4
```

* Example :


```
Employee:
  - name : Surya
    Designation : Sr Architect
  - name : Nagendra
    Designation : Vice President 

```


5. Comment 

* Syntax:

```
# This is a comment 
```

* Example :

```
# This is listing the employee 
Employee:
  - name : Surya
    Designation : Sr Architect
  - name : Nagendra
    Designation : Vice President 

```


# How to write a playbook :
1. List down all the manual steps . Run the steps and check they are working manually.

```
sudo apt-get update
sudo apt-get install openjdk-11-jdk
```
2. Playbook file will be created with an extension of .yml / .yaml

```
java.yml / java.yaml / playbook.yml / playbook.yaml
```

3. Run the playbook 

```
ansible-playbook -i /home/devops/hosts java.yml/playbook.yml
```


## Basic syntax of ansible playbook:

* Synatx: https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html
* Module : https://docs.ansible.com/ansible/2.9/modules/list_of_all_modules.html

```
---
- hosts: all/specificserver
  become: yes
  tasks: 
    - name: task1
      module:
        par1: value1
        par2: value2
    - name: task2
      module: 
        par1: value1
        par2: value2

```



# Write a playbook for installing java:
1. List down the manual steps and they are working 
```
sudo apt-get update
sudo apt-get install openjdk-11-jdk -y 
```
2. Create  file java.yml

3. Write a playbook :

* Apt Module - https://docs.ansible.com/ansible/2.8/modules/apt_module.html

```
---
- hosts: all
  become: yes
  tasks:
    - name: apt-get update step 
      apt:
        name: openjdk-11-jdk
        update_cache: yes
      
```

```
---
# Ths playbook is going to install openjdk-11-jdk 
- hosts: all
  become: yes
  tasks:
    - name: Installing Java
      apt:
        name: openjdk-11-jdk
        state: present
        update_cache: yes

```
4. Syntax check :

```
ansible-playbook -i /home/devops/hosts /home/devops/java.yml --syntax-check

```

5. Run the playbook 

```
ansible-playbook -i /home/devops/hosts /home/devops/java.yml
```

6. Dry run the playbook:

```
ansible-playbook -i /home/devops/hosts /home/devops/java.yml --check

```

* while running playbook , Bydefault task of gatheringfacts will be run initially and after that our playbook tasks will start running .

* changed -- it has done some changes on the ansible node 
* ok - No changes made 
* Ansible has the capability of check the state , before running the task 