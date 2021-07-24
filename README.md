# Git & GitHub for Software Engineers
Let us take a look at what is Git and GitHub and learn the working mechanism and differences between the two

## Git vs GitHub: Learn the Difference
First things first: Git and GitHub are two totally different software: the former lets you control the versions of your source code locally and gives you access to the history of your code stagings and commits, whereas the latter is a free of cost cloud-based hosting service for your source code

Remember, in git, everything is local, i.e., you track the progress and history of your code on your computer, in your local disk / drive. But, when you "push" your code, you are basically using GitHub for getting cloud-based hosting

Git works very beautifully in collaboration with GitHub, so not only can you control the versions of your code but also host it for absolutely free

## Git vs GitHub: Learn the History
Linus Torvalds, the guy who pioneered Linux Kernel and Linux Foundation, created the Git version controlling system in 2005. Whereas Microsoft corporation acquired GitHub in 2018 for remote cloud-based hosting, which was created in 2008 by four American programmers

## Cloning a GitHub Repository
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

### Working with Branches
Branches allow you to take your work off the master (main) branch while building up on the work already done in the main branch

* To **create a new branch,** you can use the command ``` git branch <name> ```

* To **see all the branches,** use the command ``` git branch -a ```. This also lets you know what branch you are on, as it puts an asterisk next to the branch that you are currently on

* You can use the command ``` git checkout <branch name> ``` to **switch to a specific branch.** Remember, the new sub-branch branch will have everything on the previous parent branch as well as the new changes that you make on the sub-branch branch

* Use the command ``` git switch - ``` to **switch back** to the parent branch. You will see all your changes (made in the sub-branch branch) will be "deleted" from your local file system, because they were not made in this branch. The will be "un-deleted" if you switch back to the same sub-branch

* If you want to **delete a sub-branch** which is not merged, use the command ``` git branch -D <branch name> ```. If the sub-branch is merged, then use the command ``` git branch -d <branch name> ```. Notice that we have replaced -D with -d in case the branch is already merged

* While **merging branches,** you should be on that branch in which you want to merge (the parent branch). If merging happens and a **fast forward** message is given to you by Git via terminal, it means that there had been no work done on the parent branch (to which you are merging) since you created the sub-branch (the branch that you are now merging to the parent)

* If there are **merge conflicts,** choose what you want to keep in the file and what you don't. After that commit again. This commit will be much like a merge commit, so you don't have to give any commit message

# Scratching Surface of GitHub for Remote Collaboration
As mentioned above, GitHub allows us to collaborate remotely and also hosts our source code free of cost. Only one concept, viz. forking, is discussed down below

### Forking a Repo for Contributions
Forking is done for contributing to somebody else's code. You fork their repo to your own account, which creates a copy of their repo to your account. Then, you clone it to your computer and start working on it. When you are done working, you send a merge request to the owners of the actual repo that you forked. If approved by the remote repo owners, it will be added to the actual repo (from where you forked). Else, it will be discarded
