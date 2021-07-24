# Git & GitHub for Software Engineers
Let us take a look at what is Git and GitHub and learn the working mechanism and differences between the two

## Git vs GitHub: Learn the Difference
First things first: Git and GitHub are two totally different software: the former lets you control the versions of your source code locally and gives you access to the history of your code stagings and commits, whereas the latter is a free of cost cloud-based hosting service for your source code

Remember, in git, everything is local, i.e., you track the progress and history of your code on your computer, in your local disk / drive. But, when you "push" your code, you are basically using GitHub for getting cloud-based hosting

Git works very beautifully in collaboration with GitHub, so not only can you control the versions of your code but also host it for absolutely free

## Git vs GitHub: Learn the History
Linus Torvalds, the guy who pioneered Linux Kernel and Linux Foundation, created the Git version controlling system in 2005. Whereas Microsoft corporation acquired GitHub in 2018 for remote cloud-based hosting, which was created in 2008 by four American programmers

## Cloning GitHub Repositories
When we clone a GitHub repository locally after creating it on GitHub remotely, we basically ask Git to track all the changes that we are making to the local file system. Git Desktop creates a .git folder (hidden by default in Linux distros) in the root of our project folder for tracking purposes

# A Deeper Dive into Git for Version Control
There are three phases in the life cycle of a project in which Git works for version control of our local software:

**1. Observing Modifications:** This is done by the Git for Desktop software automatically. It sits in the root folder, and it tracks all the changes made to the entire sub-tree (file system)
  
**2. Staging Modifications:** This is done by adding to the modified files an implicit flag, which lets Git know that you want to commit them. To stage our changes, we use the following commands: ``` git add <file name> ``` or ``` git add .```. Notice that the first command lets you stage a particular file, whereas the second command lets you stage all the modified files in the file tree

**3. Committing Stagings:** Finally, we commit our stagings locally using using the following command: ``` git commit -m "Your commit message goes here" ```. Notice the -m flag in the command: it lets you add a message that will be printed in the remote repository

## Controlling Versions of Our Chain
There are three very important commands that allow us to control the versions of our Git branches. In this section, we refer to the "ID" of the commits. For each of your commits, these IDs can easily be obtained by running the following command: ``` git log --oneline ```. Let us list all of three of them down below: 

**1. Checking a Commit**

``` bash
  git checkout <id>
```
  
This command lets you go back to the state of the previous commits. This will temporarily "delete" files from your computer. If you want to undo this and go back to the latest commit, just use the following command: ``` git switch - ```. This will not affect your pushes, and you will only be playing along with the files locally (using Git). This command is totally safe, but so is not the case with the next two commands mentioned in this section

**2. Reverting a Commit**

``` bash
  git revert <id>
```

This command lets you revert a commit by using its ID. So, anything that you did in that commit (and only in that commit) and not in the ones which follow that commit, will now be gone. Now, if you push after reverting, it will be changed in the remote repo as wel, i.e., changes for the push that you are reverting will be removed from there

Suppose you revert commit "ABC" from the chain. Now, still you can check it out locally using the checkout command. The reverted files will be brought back to your file system by Git


**3. Resetting the Branch to Previous Commits**

``` bash
  git reset <id> --hard
```
  
This command is dangerous and should only be used when really needed. It deletes the entire chain (starting from the last commit) till the commit whose ID you are adding in the command. Also, if you push now (with the "forceful" flag denoted by -f, so that the command becomes ``` git push -f ```), everything will be deleted from the remote repository and, your code will be taken to that ID to which you have reset your branch. You will lose all your work, literally, locally as well as remotely

**Note:** The difference between revert and reset should be very clear: revert just removes commits against a specific commit ID, whereas reset deletes everything committed on the chain after a particular commit
