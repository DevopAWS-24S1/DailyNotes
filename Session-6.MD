# Recap :
* GIT - DVCS
* Repo's : 
    1. Local - git init .
    2. Remote - github
* Three phases of git :
    1. Working Area
    2. Stagging Area
    3. Local Repo
    4. Remote Repo
* git status 
* git add <filename>
* git commit -m "message"
* git config --global user.name "username"
* git config --global user.email "useremail"
* git push origin master 
* git remote add origin <repourl>
* git clone  -- get whole code repo 
* git pull   --  get latest changes 

# Configurations overlook:
* git config --list 
* git remote -v 
* git remote set-url origin <repourl>

# untracked and modified files in git :
* Modified file - The files is already present and you have made some changes to it 
* Untracked file - It is the brand new file created 

```
git add <filename>
```
* Started developmet for the day , about to logout , add only modified files :
```
git add -u >> add all your modified files  to the staing area 
git add -A 
git add --all 
```

# Authentication Troubleshoot:
* Username & password will be stored in the credential manager >> Windows credentials
* SHH and GPG keys in the Github UI 


# Tracking changes & Travel back to the history 
* How to see the changes made to the local repo :
```
git log 
git log --online 
git checkout commitid
git checkout master
```

# Head Vs Detached head 
* Head will be alwasy at thee latest commit .
* If you are moving back to the history using the commitid , the head will be deatched and move to the respective commitid

# Move back the changes from statggngArea to WorkingArea  & also remove changes from WorkingArea:
* git reset <filename>
* git checkout <filename>
# Note: git checkout is going to work on only the modified files

# Move back the changes from staggingArea to W0rkingArea and removes changes in WorkingArea at at one shot:
* git reset --hard

# Move back the changes from localrepo to the workingArea:
* git revert <commitid>
* git revert is going revert the whole changes you have made with that commitid 


# Serving application/code to the multiple clients:
* Cant server the same code to the multiple clinet 
* Each client will have their own requirements 
* Hospital Billing - Appolo, Medplus, Yoshoda 
* Repository - Branches - three branches 
* By default the master branch is created while creating thr repository
* To create branch , list branch , switch branch

```
git branch >> list the available branches 
git branch <branchname>
git checkout branchname
git checkout -b branchname
```