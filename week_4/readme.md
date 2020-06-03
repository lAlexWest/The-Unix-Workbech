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

# Important Git Features

## Gitting Help, Logs and Diffs

- Git commands have their own man pages. You can access them with git help command. Like this example:
```
# Manual for 'status' command
git help status
```
- To see list of Git commits enter log command. Each commit has its time, date, and commit message recorded, along with a SHA-1 hash that uniquely identifies the commit.
```
git log
```
- Git can also help show the differences between unstaged changes to your files compared to the last commit. For example:
```
echo "## New line to readme.md file" >> readme.md
git diff readme.md
```
- Remove changes of not commited file to last commit:
```
git checkout readme.md
```
## Ignoring files

-  A file in Git repository called .gitignore can list names of files and sub-folders, or simple regular expressions (whatever you can use with ls) in order to specify files which should never be tracked. Each line of a .gitignore file should specify a file or group of files that should not be tracked by Git.
```
# Create passwords
echo "passwords" > passwords.pass

# Do not track passwords
echo "*.pass" > .gitignore
```

## Summary

- Git help allows you to read the man pages for specific Git commands.
- Git log will show you your commit history.
- Git diff displays what has changed between the last commit and your current untracked changes.
- You can specify a .gitignore file in order to tell Git not to track certain files.



