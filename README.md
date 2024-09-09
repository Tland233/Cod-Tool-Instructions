# GitHub-Tutorial-Template
*Author: [Eric Udlis](http://ericudlis.com)*

This Tutorial is based on the one from [hubspot](https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners)

This is a template Repo to teach the basics of contributing to a repository in Badgerloop

# How to Use This Guide

Click the "Use this template" button in the top row to copy this readme over to a new repository. Follow the instructions below and enjoy!

**If the top left of your repository screen says badgerloop-software/github-tutorial-template you have not properly created a template. Do not make any pull requests to this repository**

# Instructions (Start Here)

## Step 0: Install Git

Download git [here](https://git-scm.com/downloads). Follow the walkthrough, all default options should be good. Don't touch them unless you know what you're doing.

## Step 1: Clone the Repository
No matter what project you're working on in Badgerloop, you will always be working in a repository (Repo for short). To use git we'll be using the terminal. Check out some tutorials on the wiki. In this guide you will need to know the following.
```
Bucky@Badgerloop~$: ls    // Lists the files and directories in your current directory
Bucky@Badgerloop~$: cd    // Navigates to directory use `cd ..` to navigate up a directory
Bucky@Badgerloop~$: pwd   // Prints your working directory
```
We already have code up on GitHub so the first step is to "clone" a copy of what we have on your local machine. To begin, open up a terminal (on windows use Git Bash or WSL to follow the commands used in this tutorial) and navigate to where you'd like your project to be located. If you have a "projects" folder, this would be the place. This command will navigate you to your home directory
```
Bucky@Badgerloop~$: cd ~ 
```
Next grab the clone link from the GitHub Page. You will need to navigate to the actual webpage of the git repository on GitHub. You can find a list of all Badgerloop Repos by [clicking here](https://github.com/badgerloop-software/). If you're reading this on the GitHub page, just click the green button in the upper right that says "Clone or Download". Copy that link to your clipboard, we'll need it in the next step.

Finally, execute a git clone command to copy the repository to your local machine by typing
```
Bucky@Badgerloop~$: git clone gitLinkHere
```
This will create a directory with the most up to date version of the repository. Simply navigate into it and you will be inside the repository. Run `git status` to make sure you are in a valid git repo.
```
Bucky@Badgerloop~$: git status
On branch master
Your branch is up-to-date with 'origin/master'.
```
## Step 2: Create a seperate Branch
Before we make any commits, we have to talk about branching. Say you want to make a new feature but are worried about making changes to the main project. This is where **git branches** come into play.

One important branch is the **master** branch. This is reserved for our production ready code. Generally, you finish a feature before making it a part of master. On all Badgerloop Repos this is a locked branch requiring a review in order to make changes to master.

Branches allow you to move back and forth between different "states" of a project. All work done in Badgerloop will take place in a seperate branch before being a part of master. This way each member can work on a sub-project without interfering with other's work.

Let's create a branch by using the `git checkout` command with the `-b` flag. Let's create a branch called `{yourname}_tutorial` and confirm with the `git branch` command.

```
Bucky@Badgerloop~$: git checkout -b Eric_tutorial
Bucky@Badgerloop~$: git branch
* Eric_tutorial
  master
```
## Step 3: Add a new file to the Repo
Let's add a new file to the project. For this we are going to use the `touch` command. `Touch` will create an empty file. Create a text file titled by your first name.
```
Bucky@Badgerloop~$: touch Eric.txt
Bucky@Badgerloop~$: ls
README.md Eric.txt
```

After creating the new file, you can use the `git status` command to see which files git knows about.

```
Bucky@Badgerloop~$: git status
On branch Eric_tutorial
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        Eric.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
Basically, this means "Hey, we noticed you make a new file called Eric.txt but unless you use the `git add` command, we aren't going to do anything about it.

## Step 3.5: The Staging Enviroment
Git works on a concept called the staging enviroment, this is one of the most confusing parts of git. Let's go through some terminology.

### Commit
A commit is a record of what files you have changed since last time you made a commit. Essentially you make changes to the repo (either by adding, deleting, or modifying files) and you "commit" to your changes by telling git to put those files into a commit.

This is where the version control comes in. You can backtrack to any previous commit at any point.

### Staging Enviorment
So, how do you tell git which files to put into a commit? This is where the staging enviroment comes in. As seen in Step 2, when you make changes to your repo, git notices that a file has changed but won't do anything with it. **Git will not automatically add your files to a commit**

## Step 4: Add a File to the Staging Enviroment
Add a file to the staging enviroment by using the `git add` command
```
Bucky@Badgerloop~$: git add Eric.txt
Bucky@Badgerloop~$: git status
On branch Eric_tutorial
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   Eric.txt
```
## Step 5: Commit Your Changes
It's time to create your first commit!

Run the `git commit -m "{Your commit message}` command.

The `-m` flag means the next string will be a commit message. It is important to create meaningful commit messages so everyone knows what changes were made. It could be a new feature, fixing a bug, or even just fixing a typo. Please, please, please dont type "asdfasdfasdf" or "whatever". 

```
Bucky@Badgerloop~$: git commit -m "Added Eric.txt to mark my contribution"
[Eric_tutorial (root-commit) b345d9a] Added Eric.txt to mark my contribution
 1 file changed, 1 insertion(+)
 create mode 100644 Eric.txt
 ```

 ## Steep 5.5: A Better Way

 When working with several files, it gets tedious to add every single file for one commit. An easier way to commit several files is to run the `git commit` command with the `-am` flag. As we learned eariler `-m` means you're adding a message to your commit. The `-a` flag means you want to add all untracked files. You could combine steps 3 and 4 by only using this command.

 ```
 Bucky@Badgerloop~$: git commit -am "Added Eric.txt to mark my contribution"
 [Eric_tutorial (root-commit) b345d9a] Added Eric.txt to mark my contribution
 1 file changed, 1 insertion(+)
 create mode 100644 Eric.txt
 ```

## Step 6: Push a branch to GitHub

Now that we are done with our change, we are ready to **push** it to GitHub. This allows other people to see the changes you've made, and eventually be put into master.

To push changes on a new GitHub Branch we'll use the `git push origin {your branch name}` command. Origin is just an alias for the repository's url.

```
Bucky@Badgerloop~$: git push origin Eric_tutorial
Counting objects: 3, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 313 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/Badgerloop-Software/github-tutorial.git
 * [new branch]      Eric_tutorial -> Eric_tutorial
```

At this point it may ask you to log in with your username and password.

Finally, if you refresh the GitHub page, you'll see a note of recently pushed branches, yours may be there, or click the "branches" link to see your branch listed there.

## Step 7: Creating a Pull Request

A pull request (or PR) is a way to alert the team leads that you want to make some changes to the codebase. It allows them, as well as other Badgerloop members to review the code and make sure it looks good before putting your changes on the master branch.

To start a pull request. Click the "New Pull Request" button on next to your branch.

![pull request image](https://i.imgur.com/ODualXT.png)

Be sure to give your PR a meaningful title and description. On the Software team we have a checklist of self-checks to go through before you post a PR. You may see a big green button at the bottom that says "Merge Pull Request" Clicking this means you'll merge your changes into the master branch. 

***Note If you are doing this tutorial as part of a Software Meeting, you will be required to get a review as if it was a real PR***

Note that this button won't always be green. In some cases it'll be grey, which means you're faced with the dreadded *merge conflicts*. This is when there is a change in one file the conflicts with a change somewhere else (either in that file or elsewhere) and git can't figure out which version to use. You'll have to manually go in an tell git which version to use.

Once the button is green, go ahead and click it. This will merge your changes into the master branch. When you're done, click delete branch as well. This will help with clutter.

## Step 8: Update the Files on Your Computer

Right now the repo on GitHub looks a little different than what you have on your computer. For example, the merge commit you just made doesn't exist on your local machine. We need to get the most recent changes with a `git pull` command.

```
Bucky@Badgerloop~$: git checkout master
Switched to branch 'master'
Bucky@Badgerloop~$: git pull
remote: Counting objects: 1, done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), done.
From https://github.com/badgerloop-software/github-tutorial
 * branch            master     -> FETCH_HEAD
   b345d9a..5381b7c  master     -> origin/master
Merge made by the 'recursive' strategy.
 Eric.txt | 1 +
 1 file changed, 1 insertion(+)
 ```

## Step 9: Give yourself a Pat on the Back

Yahoo, you've sucessfully contributed to a repository! Congratulations, this is the foundation of writing code for the Badgerloop teams and will be used nearly every time you work with Badgerloop Software.

Good luck in your future quest to git gud :)
