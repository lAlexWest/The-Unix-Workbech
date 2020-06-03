# Git and GitHub Basics
## What are Git and GitHub?
- Git is a command line program which allows you to track versions of any code or plain text documents that you create.
- Git organizes groups of files that you’re tracking into a repository, which is just a directory where all of the changes to files in that directory are tracked.
- GitHub is a website that provides remote Git repositories. A remote repository is just a Git repository that you’re able to access over an internet connection. 
- GitHub also makes it easy to jump in and help somebody with their project.

## Setting Up Git and GitHub

Check version and set two environmental variables (do once):
```
git --version

# Set user name (your GitHub user name)
git config --global user.name "UserName"

# Set Email (your GitHub email)
git config --global user.email MyEmail@email.com
```

## Getting started with Git

### Create repository
1. Create directory
```
cd ~
mkdir my_project_name
cd my_project_name
```
2. Initialize repository
```
git init
```
3. Create file and start tracking(staging) it
```
echo "# Project Name" > readme.md
```
### Tracking and commits
- To check status use following command
```
# prints untracked and tracked files
git status
```
- To start tracking files:
```
# track file
git add readme.md

# or track all files
git add -A
```
- To remove file from track:
```
git rm --cached readme.md
```
- To commit(create milestone of our changes):
```
git commit -m "Message describing your changes"
```
- Undo most recent commit:

```
# Probably not best way to do it (rmk)
git reset --soft HEAD~
```

## Summary
- Git tracks changes to plain text files (code files and text documents).
- A directory where changes to files are tracked by Git is called a Git repository.
- Change your working directory, then run git init to start a repository.
- You can track changes to a file using git add [names of files].
- You can create a milestone about the state of your files using git commit -m "message about changes since the last commit".
