# Git frequently used commands

## delete branch locally
git branch -d localBranchName

## delete branch remotely
git push origin --delete remoteBranchName


## List your existing remotes
git remote -v

## Change a remote Git repository
git remote set-url private https://github.com/ahmadaking/Coffee-Leaves-private.git

## list the available remotes and their URLs in the folder
git remote -v

## Delete a remote repo
git remote remove [remote name]



## How do I copy a version of a single file from one Git branch to another?
## Run this from the branch where you want the file to end up:
git checkout otherbranch myfile.txt

## Sync local repo with the original on GitHub 
git remote -v
git fetch "upstream"
git merge "pstream"/master
