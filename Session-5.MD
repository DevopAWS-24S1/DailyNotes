# Git 
* Git is a place where developers store the code , devops can also store the script
* Git is a distributed version control system

# Evolution of git :
* Share the code by email
* Sharedfolder- accessible over internet 
* Lot of evolutions in the development 
* Centralised version control system & Distributed Version control system 

# In cvcs
* Need a client to connect to the CVCS 
* Cant work offline
* Have to connect to nternet all the time to work on the code
* DR and backup has to be managed 

# In DVCS :
* Dont need any client 
* Can work offline
* Internet is required only when you raee pushing the code to the DVCS
* Each laptop of the developer acts as a DR or backup


*  Git is DVCS 
# Major features of the git :
* Track changes 
* Track back to the history 
* Serving code to the multiple clients 
* Parallel development 

# Repositories in git :
* user , cart , favourites , catagories .......
* Best usecase is developing single service in single repository
* Cases where multiple services are also developes in a single repository 

1. Local Repository   -- In your laptop
2. Remote Repository  -- In github, remote website 


* Github, Gitlab, Bitbucket 

# Local Repository 
* If you want to create local repository 

```
mkdir MyLocalRepo
cd MyLocalRepo
git init 
```

# Remote Repository:
* In Github, Gitlab, Bitbucket 
1. Login in to the Github >> Navigate to repositories >> Click on New Repository 
    ```
    * Repo name 
    * Description
    * public/private
    * Check the README.md file creation
    * Create Repository 
    ```

# Copy code from Remote Repo to the Local laptop 
1. Clone  - New Developer 
2. Pull   - Existing Developer , you have the code on your local , but you dont have latest changes 


# Copy the code from Local Repo to the Remote Repo 
1. Push  - Copy the code from Local repo to the remote repo 


# Three Phases in git :
1. Working Area
2. Stagging Area 
3. Local Repo 
4. Remote Repo

# Create a file in the working tree , send the file till the local repo
* cd MyLocalRepo
* touch gitpractice.txt
* git status - change made in the working tree/Area
* git add gitpractice.txt -- Add the file from workingtree to stagging areea
* git commit -m " crated gitpractice file" 
* when you are trying to commit , need to provide/configure your loal repo with the username/email of the github account 

```
 git config --global user.email "you@example.com"
 git config --global user.name "Your Name"

```
* All your changes in the local repo will be stored in  ```.git``` folder

* git push - copy the code from local repo to remote repo 

* Configure local repo to the remote repo 
```
git remote add origin <<remoterepo https url>>
```
* git push origin master  -- push the code from local repo to the remote repo 
* while pushing there are two ways 
1. Sign with browser
2. Sign in with code 


# Git clone 
* git clone is going to copy the code from the remote repo to the local repo 
1. https - sign in with browser /signin with code
2. ssh   - exchange keys from laptop to the github

# How to create shh and copy to github:
1. In your laptop -- ```ssh-keygen```
2. Copy the content of pub file and go in to the ssh keys configuraion in github and configure your pub key .


# Git pull :
* going to get the latest changes from github 



# Overall git commands till now :
```
git status 
git add <filename>
git commit -m "message"
git config --global user.name <usernamee>
git config  --global user.email <email>
git push 
git remot add origin repourl
git push origin master
git clone
git pull

```