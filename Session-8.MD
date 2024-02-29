# Fastforward Merge :
* The basic behaviuor of fast forward merge is , the head will move and look at the latest branch commitid.
```
git checkout company-z
git merge company-z
git log 

git merge --no-ff company-z 
```

# Rebase:
* It is going to change the base of the branch 
```
git checkout company-a
git rebase commitid
```

# Cherry-pick:
* If you want to pick some specific commitid feature from another branch , you can use cherry-pick
```
git checkout branch-a
git cherry-pick commitid
```

# stash:

* It is going to store your changes in the temporary place.

```
git checkout branch-a
touch stash.txt
git add -A
git stash 
git stash pop
```


# Blame:
* It helps us in getting the information of who made last  changes to this file along with commit id and timestamp.
```
git blame <fileename>
```

# Branching Strategy 

# Fork :
* It copies the whole repo to your account from others account 
