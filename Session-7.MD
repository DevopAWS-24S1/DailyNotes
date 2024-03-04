# Branches :
    1. Local branches 
    2. Remote branches
* git branch >> list of branches in the local 
* git branch -r >> list remote repo branches 

# Push the company-x branch to remote repo:

```
git checkout company-x
git push origin company-x
git checkout company-y
git push origin company-y
```

# Delete the branches :
## Deleting local branches :
* git branch -d branchname
* git branch -D branchname >>  force deleted

## Delete the remote branches 
* git push origin -d branchname
* git push origin -D branchname >>  force deleted

# Git tracks the removal/deletion of file as well

```
rm pull
git status 

```

# Git tracks folder or not ..?
* Git track the folder , if it has file in it . 
* Git doesnot track empty folders.

# Merge 
* Merge is going to help us in combining the code between two  branches
* get in to the branch in which you wanted to merge:
```
git checkout company-x
git merge company-y
git log 
```

# Merge Conflicts :
* A Merge conflict occures whilee two developers are working on a same code and in the same file .
1. Create two folders
```
mkdir developer1
mkdir developer2
```
2. clone the code in to the developer1 folder
```
git clone repourl
```
3. clone the code in to the developer2 folder
```
git clone repourl
```
4. Make some changes to a file 1.txt in developer1
```
add content to 1.txt 
git add -A ; 
git commit -m ""
git push origin master
```
5. 4. Make some changes to a file 1.txt in developer2
```
add content to 1.txt 
git add -A ; 
git commit -m ""
git push origin master

git pull 
* merge conflict arises here 
vi 1.txt >> take a call whose code to be present
git add -A
git commit -m ""
git push origin master 
```
