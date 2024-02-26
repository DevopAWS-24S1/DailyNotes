# Continue to te CRUD operatins"
* id -u >> useid of the user 
* sudo su -  >> siwtch to the root user 
* sudo su - ubuntu >> switch to the unber user and home path of ubuntu 

* cut & awk - used to cut the string or cut the file
* cut -d ":" -f 1 passwd  >> provide the list of users 
* cut -d ":" -f 3 passwd  >> provide list  userid 
* cut -d ":" -f 3 passwd  >> provide the list of users and userids as well

* awk -F ":" '{print $1}' passwd  >> provide the list of users
* awk -F ":" '{print $NF}' passwd >> Print last separation
* awk -F ":" '{print $1,$3}' passwd >> provide the list of users and userids as well

# update:
* vi editor 
* In VI there ate three mode
        1. : mode
        2. Esc mode
        3. Insert mode 
* shif + G  >> end of the file 
* gg >> to go to top of the file 

## : mode :
* :/ - search from top 
* :? - search from bottom 
* :set nu - linenumber to your file 
* :set nonu -- unset linenumbers
* :q - exit without saving the content 
* :q! - force exit 
* :s/searchword/replaceword/g >> replace the word 
* :s/searchword/replaceword/gc >> replace the word with confirm
* :wq >> save the file 
* :wq! >> force save the file 


## Ecs mode :
* u - undo 
* yy - copy
* p - paste 
* 2p - paste 2 times 
* dd - delete the line 

## Insert mode 
* Insert - for editing/writing the file 


```
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
daemon x 1 1 daemon /usr/sbin /usr/sbin/nologin - :  as delimiter 
daemon:x:1:1:daemon: usr sbin: usr sbin nologin / as delimiter 

```
* cut -d ":" -f 1 

# Instance States:
1. Running state 
2. Stop state 
3. Terminate state 
4. Reboot state 

* /etc/passwd - all users information
* userid of root is always 0 
* For all other user we create on it starts from 1000 and morethan 1000
* Below 1000 those are system user 


# Permissions in Linux:
*  chmod 740 Devops.txt

```
-rwxr----- 1 ubuntu ubuntu 0 Feb 21 06:22 Devops.txt
```
```
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 21 06:22 Devops.txt
user  - u 
group - g 
other - o 
* User belongs to devops group , other people like developers/testers they and write the file
* R - 4 
* W - 2 
* X - 1

```
* chown -R username:username Devops.txt

# Management
1. UserManagement 
2. PackageManagement
3. ProcessManagement
4. ServiceManagement
5. Networkmanagement

## 1. UserManagement
* adduser username >> user creation
* passwd username >> reset the password , but you should in root to do it 
* By default AWS servers comes with password based authentication disabled .
* To enable paswword based authentication :
        1. Go to /etc/ssh/sshd_config >> Change passwordAuthentication yes in the line 57 
        2. sudo service ssh restart 
        3. sudo service ssh status 
* try to connect usinf devosp user 
```
ssh devops@publicip
```
* addgroup groupname
* adduser username groupname  >> add user to the group
* group username  >> list user groups 