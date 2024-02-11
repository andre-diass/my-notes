# Git and Github

**Created:** April 24, 2023 7:45 PM  
**Updated:** February 11, 2024 6:33 PM

## MAIN OPERATIONS

```bash
git add .
git commit <file name> -m "comment"
git push -u origin <branch name>

git checkout -b <branch name>
git switch <branch name>
git branch
git branch -M <branch name>

git clone <repository link>
git clone -branch new_feature <repository>
git pull

git restore --source <hash code> < . or file name>

git log --oneline
git log -p
git log --author="user_name"
git log --since=1.month.ago --until=1.day.ago
```
## LOCAL REPOSITORY (a .git file)
```bash
git init                    # create a git local repository inside the working directory
git status                  # to see what's currently in the staging area
git add <file name>         # to add the file to the staging area
git add .                   # to add all files inside the current directory
git rm --cached -r          # to remove files from the staging area
git commit -m "change"      # to commit files to the local repository
git log                     # to see commits
git diff <file name>        # to see differences between saved files
git checkout <file name>    # to get the last committed file to substitute the current one
```
## REMOTE REPOSITORY (the .git directory)
```bash
Copy code
git remote add origin <url of remote repository>   # to transfer or push existing local repository
git push -u origin master                         # to push local repository to remote repository
TO HIDE FILES
bash
Copy code
touch .gitignore    # create a .gitignore file to specify files to hide
MANAGE BRANCHES
bash
Copy code
git branch <branchName>         # create a new branch
git branch                      # see branches
git checkout <branchName>       # switch branches
git merge                       # merge branches```
