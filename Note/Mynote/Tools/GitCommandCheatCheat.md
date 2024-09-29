# Git Command Cheat Sheet

## Table of Contents
- [Clone a repository](#clone-a-repository)
- [Push a project](#push-a-project)
- [Delete a Branch](#delete-a-branch)
- [Go Back to the Previous Commit](#go-back-to-the-previous-commit)
- [Check the current branch](#check-the-current-branch)

## Clone a repository
To clone a repository to your local machine:
```bash
git clone "https://github.com/your-username/your-repo.git"
```

## Push a project
1) Create a new branch and switch to it:
```bash
git checkout -b "your_branch_name"
```
2) Check the status of the files:
```bash
git status
```
3) Add all files to the staging area:
```bash
git add *
```
4) if you want to add singullar file:
```bash
git add path/path/filename
```
5) Commit your changes with a message:
```bash
git push origin "your_branch_name"
```
6) Push your branch to the remote repository:
```bash
git push --set-upstream origin "your_branch_name"
```

## Delete a Branch
1) To delete a branch locally:
```bash
git branch -d "branch_name"
```
2) delete branch remotely:
```bash
git push origin --delete "branch_name"
```

## Go Back to the Previous Commit
1) View your commit history:
```bash
git log
```
2) previous commit and keeps changes in the working directory( soft reset):
```bash
git reset --soft HEAD~1
```
3) remove all changes (hard reset):
```bash
git reset --hard HEAD~1
```

## Check the current branch
```bash
git branch
```