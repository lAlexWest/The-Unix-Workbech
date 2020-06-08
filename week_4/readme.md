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
- To remove file from track (before committing):
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
# Manual for "status" command
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
## Example: Which day of the week most of the commits occured on.
```
git log | grep "Date: " | cut -d " " -f 4 | sort | uniq -c | sort -rn 
```

## Summary

- Git help allows you to read the man pages for specific Git commands.
- Git log will show you your commit history.
- Git diff displays what has changed between the last commit and your current untracked changes.
- You can specify a .gitignore file in order to tell Git not to track certain files.

# Branching

## Creating Branches

- Branching is one of the most powerful features that Git offers. Creating different Git branches allows you to work on a particular feature or set of files independently from other “copies” of a repository. That way you and a friend can work on different parts of the same file on different branches, and then Git can help you elegantly merge your branches and changes together.
- To get list of all available branches:
```
# the "*" indicates which branch you're currently on
git branch
```
- The default branch that is created is always called master. Usually people use this branch as the working version of the software that they are writing, while they develop new and potentially unstable features on other branches.

- To add a branch we’ll also use the git branch command, followed the name of the branch we want to create:
```
git branch name-of-new-branch
```
- To change the branch:
```
git checkout name-of-the-branch

# or create and change branch

git checkout -b name-of-the-branch
```
- To delete branch:
```
git branch -d name-of-the-branch
```
- Example of branch usage:
```
echo "# Master branch" > readme.md
git add -A
git commit -m "master branch commit"

git checkout -b password-feature
echo "# Password-feature branch" > readme.md
git add -A
git commit -m "new feature branch commit"
```

## Merging branches and resolving conflicts
- Now that we’ve made a couple of changes to readme.md, let’s combine those changes with what we have in the master branch. This is made possible by a Git merge. Merging allows you to elegantly combine the changes that have been made between two branches. Let’s merge the changes we made in the password-feature branch with the master branch. Git incorporates other branches into the current branch by default. When you’re merging, the current branch is also called the base branch. 
- Example of merging:
```
echo "# Master branch" > readme.md
git add -A
git commit -m "master branch commit"

git checkout -b password-feature
echo "# Password-feature branch" >> readme.md
git add -A
git commit -m "added new content that doesnt modify our master branch contents"

git merge password-feature
```
- But what if there are two commits in two separate branches that make different edits to the same line of text? When this occurs it is called a **conflict**. Example of conflict and its resolving:
```
# Creating conflict

echo "# Master branch" > readme.md
git add -A
git commit -m "master branch commit"

git checkout -b password-feature
echo "# Password-feature branch" > readme.md
git add -A
git commit -m "changed 1 line to create conflict"

git merge password-feature

# Resolving conflict

vim readme.md # delete conflicting line
git add -A
git commit -m "resolved conflict"
```

## Summary

- Git branching allows you and others to work on the same code base together.
- You can create a branch with the command git branch [name of branch].
- To switch to a branch use git checkout [name of branch].
- You can combine a branch with your current branch by using git merge.

# GitHub

## Using GitHub you can create repository by clicking button 'Create Repository'

- GitHub offers a few suggestions about what to do with our new remote repository. We’ve already been using a local Git repository, and what GitHub provides is a remote Git repository. A remote Git repository is just a Git repository stored on a computer is that always turned on and connected to the internet, so it can act as a central point where we can share and sync our changes to files with our friends and colleagues. We can see which remote repositories our local repository is connected to with the git remote command:

```
# List of all remote repositories
git remote

# Add remote repo (origin - alias for remote repo)
git remote add origin (https or ssh address to your repo)
```

- Git push updates a remote repository with all of the commits that we’ve made to our local Git repository. This first Git push you do when setting up a remote on GitHub with a local repository is a little different from future Git pushes. We’ll need to use the -u flag in order to set origin as the default remote repository so we don’t have to provide its name every time we want to interact with it:

```
git push -u origin master
```

## Markdown

- Markdown is a markup language. Markup languages are sets of rules for adding decorative features to text. The most popular markup language is HTML, but you might have also heard of XML and LaTeX. Markdown is a powerful markup language because it’s small, intuitive, and readable when it’s written as plain text. GitHub transforms Markdown files (which end in the file extension .md) into simple HTML web pages in your repository. If there is a file called README.md in any folder in your repository, then that file is rendered to HTML and displayed on GitHub.

There are example of markdown language:
Few markdown rules:

Pound signs (#, ##) make headings.
- A word surrounded by single asterisks (*word*) makes that word italicized.
- A word surrounded by double asterisks (**word**) makes that word bold.
- You can create lists with hyphens (-) or numbers (1., 2., 3.).
- Code can be placed in the middle of a line with single backticks (`code`).
- A code block can be created by putting code in between a set of triple backticks (```).
- You can insert a link with brackets and parentheses ([Link text here](http://jhu.edu)).
- You can use an image with an exclamation point, and a link to an image (![Alt text here](http://jhu.edu/jeff.jpg))















