# gitproject

# Git Tutorial

Git is a version control language that makes it easy to track changes made by multiple people to various files. It does this by compartmentalizing changes into four data stores. The changes you make to files on your local machine are stored in the working tree. The staging area is where you add the changes from your working tree that aren't ready to be committed to your local repository, the next data store. The local repository is the copy of the final data store, the remote repository. The local repository is the finalized copy of the changes you make which can be pushed to the remote repository, which holds the centralized copy of the files and changes for everyone to access.

To move changes to filename.txt from the working tree to the staging area, use the command:
```
git add filename.txt
```
To move changes from the staging area to the local repository, use the command:
```
git commit -m "message describing your changes here"
```
To move changes from the local repository to the remote repository, use the command:
```
git push
```

The most common host for Git repositories is GitHub which is what we'll be using today.

**Cloning**
The first step to working with git is to clone a repo. Repo is short for repository and it is basically a code project. In order to clone a repo onto your local machine, open your terminal and navigate to where you want the cloned repo to be stored. In this example we'll clone the repo to our desktop. Copy the GitHub link and type this line into the terminal:
```
git clone https://github.com/williamb9090/gitproject
```
The terminal should respond with:
<a href="https://ibb.co/tQz6j4d"><img src="https://i.ibb.co/KbDg4X1/image1.png" alt="image1" border="0"></a>
Now that we have our repo cloned to our desktop, we can move on to stashing.

**Branches**
To organize the changes you make to your project, git uses branches which are different versions of the same code. Versions of code can be thought of as nodes in a binary tree with each new version becoming a child node of the previous version. When a node has two children, they are referred to as branches since both new versions are branching off of the same parent version. Lets make a new branch called new-branch:
```
git branch new-branch
```
To see a list of branches, run this command:
```
git branch
```
You should see a list like this:
<a href="https://ibb.co/XLfTvjj"><img src="https://i.ibb.co/dMsyzjj/image2.png" alt="image2" border="0"></a>
Now that we've created a branch, lets navigate to it with this command:
```
git checkout new-branch
```

Now that we're in a new branch, we can make some changes and talk about stashing.

**Stashing**
Stashing is a way to save your changes until you are ready to apply them to whatever branch you're working on. It is also useful when you realize you are on the wrong branch and need to apply the changes you've made to a different branch. First lets  make some changes to the README.md file in the repo. Run this command:
```
nano README.md
```
Lets add a line in this file so README.md looks like this:
<a href="https://ibb.co/4mFyvvN"><img src="https://i.ibb.co/NVFhDDY/image3.png" alt="image3" border="0"></a>
Save your changes and exit the file with ^X, Y, and enter. We can see the changes we've made with:
```
git diff
```
Now that we've made some changes, we can stash them with:
```
git stash save "added 'new line'"
```
This adds the change to the stash list and removes it from the actual file. If we run:
```
git diff
```
We can see that there are no actual changes in the file. We can now navigate back to main with:
```
git checkout main
```
And pop the changes from the stash to the current branch. First lets check the stash list with:
```
git stash list
```
We can see the only entry is the change we just added to the stash. To apply changes to the current branch, run:
```
git stash pop
```
"Popping" applies the first change in the stash list and removes it, but if we wanted to keep the changes in the stash list, you would run:
```
git stash apply
```
Now that we've made some changes, lets merge the branches.

**Merging**
First lets commit the changes we made on our new-branch with:
```
git commit -a -m "added a new line"
```
Now we can merge the changes by navigating back to our main branch and merging:
```
git checkout main
git merge new-branch
```
Finally we can push our changes with:
```
git push origin
```
