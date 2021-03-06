---
title: A Beginner's Guide to Git + GitHub
published: true
tags: git, github
cover_image: https://i.imgur.com/KcLnrnU.png
---

## Terminology
#### Repository
A directory or folder where your code lives.

#### Remote
The version of your repository that lives on GitHub's servers and is accessible to anyone with an internet connection. If you have a private repository, other people won't be able to access your code, but you can still access it from different machines.

#### Local
The version of your repository that lives on your computer. This may or may not be the same as your remote repository, as it depends on the last time you pushed up to GitHub or pulled down from it.

#### Fork
Forking a repository makes a copy of it and houses it on your GitHub account. For example, if I forked Sylwia's project called `sylwia/dismantle-the-patriarchy`, it would create a new repository on my account, as `isabelxklee/dismantle-the-patriarchy`

#### Clone
Cloning a repository does *not* make a copy, but instead allows you to directly download the repository on to your local machine. 

## Commands
#### git add
Adds any files that have been changed to git's staging zone so that it is ready to be committed. Think of it as adding a tracker to your file, so that git knows what has changed or been updated.

#### git commit
Saves a snapshot of your work. It's like a checkpoint that you can always revert back to. All commits are accessible on your repository and you can see the exact changes that were made.

#### git push
Sends all of your commits to GitHub so that your work isn't just living on your local machine. This command updates your remote repository to match your local one. 

#### git pull
Updates your local machine with any changes that have been made to your repository in other places. For example, if you're working with a partner, `git pull` will update your local repository with any changes that your partner has pushed up to GitHub.

#### git remote -v
Allows you to see all the remote repositories that are tracking this branch of code.

#### git status
Shows you if there are any differences between the local and remote repositories; any files that have been changed, but not tracked with `git add` yet; and any files that have been committed, but not pushed up.

Example:
```
~/Development/dev-blog-posts // ♥ > git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   beginners_guide_to_git.md
```

#### git branch
Shows you all the existing branches in the repository.

Example:
```
~/Development/dev-blog-posts // ♥ > git branch
  * master
  refactor
```

#### git branch -d <BRANCH_NAME>
Deletes a branch from your repository.

Example:
```
~/Development/dev-blog-posts // ♥ > git branch -d refactor
  Deleted branch refactor (was ed6cd03).
```

#### git checkout -b <BRANCH_NAME>
Creates a new branch.

Example:
```
~/Development/dev-blog-posts // ♥ > git checkout -b refactor
  Switched to a new branch 'refactor'
```

#### git checkout <BRANCH_NAME>
Switches to a different branch.

#### git merge <BRANCH_NAME>
Merges two branches together. If there are differences in the code between the branches, there will be a merge conflict.

## Sources
Git Documentation: https://git-scm.com
How Git and GitHub can make your life easier: https://medium.com/swlh/how-git-and-github-can-make-your-life-easier-2ff5b9e1f6f1