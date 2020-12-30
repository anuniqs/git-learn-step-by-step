
### 1. Installation —

**01 Installation**

anup@megatron:~$ sudo apt-get update

anup@megatron:~$ sudo apt-get install git

anup@megatron:~$ git --version



### 2. Preparation —

**01 Setting up name and e-mail address**

anup@megatron:~$ git config --global user.name "anuniqs"

anup@megatron:~$ git config --global user.email "bca.anup@gmail.com"

anup@megatron:~$ git config --global color.ui auto   

anup@megatron:~$ git config --global core.autocrlf input

anup@megatron:~$ git config --global core.safecrlf warn



### 3. Creating a Project —

**01 Create a “Hello, World!” page**

anup@megatron:~$ mkdir hello

anup@megatron:~$ cd hello/

anup@megatron:~/hello$ touch hello.html

anup@megatron:~/hello$ nano hello.html

```
Hello, World!
```


**02 Create a repository** 

anup@megatron:~/hello$ git init


**03 Add the page to the repository**

anup@megatron:~/hello$ git add hello.html

anup@megatron:~/hello$ git commit -m "first commit with my hello.html page"


### 4. Checking the status of the repository

01 Check the status of the repository

anup@megatron:~/hello$ git status



### 5. Making changes —

**01 Changing the “Hello, World” page**

anup@megatron:~/hello$ nano hello.html

```
<h1>Hello, World!</h1>
```

anup@megatron:~/hello$ git status



### 6. Staging the changes —

anup@megatron:~/hello$ git add hello.html

anup@megatron:~/hello$ git status

**git reset command to unstage these changes**

anup@megatron:~/hello$ git reset

anup@megatron:~/hello$ git status



### 7. Staging and committing —

anup@megatron:~/hello$ touch a.html b.html c.html

anup@megatron:~/hello$ git add a.html

anup@megatron:~/hello$ git add b.html

anup@megatron:~/hello$ git commit -m "modified:   a.html, b.html"

anup@megatron:~/hello$ git status

anup@megatron:~/hello$ git add c.html

anup@megatron:~/hello$ git commit -m "modified:   c.html"

anup@megatron:~/hello$ git status



### 8. Commiting the changes —

anup@megatron:~/hello$ git commit



### 9. Changes, not files —

**01 First Change: Adding default page tags**

anup@megatron:~/hello$ nano hello.html

```
<html>
  <body>
	<h1>Hello, World!</h1>
  </body>
</html>
```


**02 Add this change**

anup@megatron:~/hello$ git add hello.html


**03 Second change: Add the HTML headers**

anup@megatron:~/hello$ nano hello.html

```
<html>
  <head>
  </head>
  <body>
	<h1>Hello, World!</h1>
  </body>
</html>
```

**04 Check the current status**

anup@megatron:~/hello$ git status


**05 Commit**

anup@megatron:~/hello$ git commit -m "Added standard HTML page tags"

anup@megatron:~/hello$ git status


**06 Adding the second change**

anup@megatron:~/hello$ git add .

anup@megatron:~/hello$ git status


**07 Commit the second change**

anup@megatron:~/hello$ git commit -m "Added HTML header"



### 10. History —

anup@megatron:~/hello$ git log

**01 One line history**

anup@megatron:~/hello$ git log --pretty=oneline


**04 The ultimate format of the log**

anup@megatron:~/hello$ git log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short



### 11. Aliases —

**01 Define the hist alias in the .gitconfig file**

anup@megatron:~$ nano /home/anup/.gitconfig
```
[alias]

hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
```
anup@megatron:~/hello$ git hist



### 12. Getting older versions

**01 Getting hashes for the previous versions**

anup@megatron:~/hello$ git hist

anup@megatron:~/hello$ git checkout eb748d1

anup@megatron:~/hello$ cat hello.html

**02 Returning to the latest version in the master branch**

anup@megatron:~/hello$ git checkout master

anup@megatron:~/hello$ cat hello.html



### 13. Tagging versions —

**01 Creating a tag for the first version**

anup@megatron:~/hello$ git tag v1


**02 Tags for previous versions**

anup@megatron:~/hello$ cat hello.html

anup@megatron:~/hello$ git checkout v1^

anup@megatron:~/hello$ cat hello.html

anup@megatron:~/hello$ git tag v1-beta


**03 Check out by the tag name**

anup@megatron:~/hello$ git checkout v1

anup@megatron:~/hello$ git checkout v1-beta


**04 Viewing tags with the tag command**

anup@megatron:~/hello$ git tag


**05 Viewing tags in logs**

anup@megatron:~/hello$ git hist master --all



### 14. Discarding local changes (before staging) —

**01 Checking out the Master branch**

anup@megatron:~/hello$ git checkout master


**02 Change hello.html**

anup@megatron:~/hello$ nano hello.html

```
<html>
  <head>
  </head>
  <body>
	<h1>Hello, World!</h1>
	<!-- This is a bad comment.  We want to revert it. -->
  </body>
</html>
```

**03 Check the status**

anup@megatron:~/hello$ git status


**04 Undoing the changes in the working directory**

anup@megatron:~/hello$ git checkout hello.html

anup@megatron:~/hello$ git status

anup@megatron:~/hello$ cat hello.html



### 15. Cancel Staged changes (before committing) —

**01 Edit file and stage changes**

anup@megatron:~/hello$ nano hello.html

```
<html>
  <head>
	<!-- This is an unwanted but staged comment -->
  </head>
  <body>
	<h1>Hello, World!</h1>
  </body>
</html>
```

anup@megatron:~/hello$ git add hello.html


**02 Check the status**

anup@megatron:~/hello$ git status

**03 Reset the buffer zone**

anup@megatron:~/hello$ git reset HEAD hello.html

anup@megatron:~/hello$ git status


**04 Switch to commit version**

anup@megatron:~/hello$ git checkout hello.html

anup@megatron:~/hello$ git status



### 16. Cancelling commits and Removing a commit from a branch —

**01 Cancelling commits**

To cancel the commit we will create a new commit, cancelling the unwanted changes.


**02 Edit the file and make a commit**

anup@megatron:~/hello$ nano hello.html

```
<html>
  <head>
  </head>
  <body>
	<h1>Hello, World!</h1>
	<!-- This is an unwanted but committed change -->
  </body>
</html>
```

anup@megatron:~/hello$ git add hello.html

anup@megatron:~/hello$ git commit -m "Oops, we didn't want this commit"


**03 Make a commit with new changes that discard previous changes**

anup@megatron:~/hello$ git revert HEAD


**04  Check the log**

anup@megatron:~/hello$ git hist


**05 Mark this branch first**

anup@megatron:~/hello$ git tag oops


**06 Reset commit to previous Oops**

anup@megatron:~/hello$ git reset --hard v1

anup@megatron:~/hello$ git hist


**07  Nothing is ever lost**

anup@megatron:~/hello$ git hist --all



### 17. Removing the oops tag —

**01 Removal of the oops tag**

anup@megatron:~/hello$ git tag -d oops

anup@megatron:~/hello$ git hist --all



### 18. Changing commits —

**01 Change the page and commit**

anup@megatron:~/hello$ nano hello.html

anup@megatron:~/hello$ git add hello.html

anup@megatron:~/hello$ git commit -m "Add an author comment"

**02 Oops... email required**

anup@megatron:~/hello$ nano hello.html

```
<!-- Author: Anup Kumar Mondal (anuniqs@gmail.com) -->
<html>
  <head>
  </head>
  <body>
	<h1>Hello, World!</h1>
  </body>
</html>
```

**03 Change the previous commit**

anup@megatron:~/hello$ git add hello.html

anup@megatron:~/hello$ git commit --amend -m "Add an author/email comment"


**04 View history**

anup@megatron:~/hello$ git hist



### 19. Moving files —
 
**01 Move the hello.html file to the lib directory**

anup@megatron:~/hello$ mkdir lib

anup@megatron:~/hello$ git mv hello.html lib

anup@megatron:~/hello$ git status

**02 Commit new directory**

anup@megatron:~/hello$ git commit -m "Moved hello.html to lib"



### 20. More information about the structure —

**01 Adding index.html**

anup@megatron:~/hello$ nano index.html

anup@megatron:~/hello$ git add index.html

anup@megatron:~/hello$ git commit -m "Added index.html."



### 21. Inside Git: .Git directory —

**01 The .git directory**

anup@megatron:~/hello$ ls -C .git


**02 Object Database**

anup@megatron:~/hello$ ls -C .git/objects


**03 Inquire the database objects**

anup@megatron:~/hello$ ls -C .git/objects/0a


**04 Config File**

anup@megatron:~/hello$ cat .git/config


**05 Branches and tags**

anup@megatron:~/hello$ ls .git/refs

anup@megatron:~/hello$ ls .git/refs/heads

anup@megatron:~/hello$ ls .git/refs/tags

anup@megatron:~/hello$ cat .git/refs/tags/v1


**06 HEAD File**

anup@megatron:~/hello$ cat .git/HEAD



### 22. Git inside: Direct work with git objects —

**01 Searching for the last commit**

anup@megatron:~/hello$ git hist --max-count=1


**02 Display of the last commit**

anup@megatron:~/hello$ git cat-file -t 90ead67

anup@megatron:~/hello$ git cat-file -p 90ead67


**03 Tree search**



### 23. Creating a Branch —

**01 Create a branch**

anup@megatron:~/hello$ git checkout -b style

anup@megatron:~/hello$ git status

**02 Add style.css file**

anup@megatron:~/hello$ touch lib/style.css

anup@megatron:~/hello$ nano lib/style.css

```
h1 {
  color: red;
}
```

anup@megatron:~/hello$ git add lib/style.css

anup@megatron:~/hello$ git commit -m "Added css stylesheet"

**03 Change the main page**

anup@megatron:~/hello$ nano lib/hello.html

```
<!-- Author: Anup Kumar Mondal (anuniqs@gmail.com) -->
<html>
  <head>
	<link type="text/css" rel="stylesheet" media="all" href="style.css" />
  </head>
  <body>
	<h1>Hello, World!</h1>
  </body>
</html>
```

anup@megatron:~/hello$ git add lib/hello.html

anup@megatron:~/hello$ git commit -m "Hello uses style.css"

**04 Change index.html**

anup@megatron:~/hello$ nano index.html

```
<html>
  <head>
	<link type="text/css" rel="stylesheet" media="all" href="lib/style.css" />
  </head>
  <body>
	<iframe src="lib/hello.html" width="200" height="200" />
  </body>
</html>
```

anup@megatron:~/hello$ git add index.html

anup@megatron:~/hello$ git commit -m "Updated index.html"

anup@megatron:~/hello$ git hist --all



### 24. Navigating Branches —

**01 Switching to the Master branch**

anup@megatron:~/hello$ git checkout master

anup@megatron:~/hello$ git branch

anup@megatron:~/hello$ cat lib/hello.html


**02 Let us return to the style branch**

anup@megatron:~/hello$ git checkout style

anup@megatron:~/hello$ git branch

anup@megatron:~/hello$ cat lib/hello.html

**01 Update the README file with the changes**

anup@megatron:~/hello$ nano README

```This is the Hello World example from the git tutorial.```

**02 Commit changes of README file in the master branch.**

anup@megatron:~/hello$ git checkout master

anup@megatron:~/hello$ git add README

anup@megatron:~/hello$ git commit -m "Added README"



### 25. View the different branches —

**01 View current branches**

anup@megatron:~/hello$ git hist --all



### 26. Merging —

**01 Merging to a single branch**

anup@megatron:~/hello$ git checkout style

anup@megatron:~/hello$ git branch

anup@megatron:~/hello$ git merge master

anup@megatron:~/hello$ git hist --all



### 27. Creating a conflict —

**01 Return to the master and create conflict**

anup@megatron:~/hello$ git checkout master

anup@megatron:~/hello$ nano lib/hello.html

```
<!-- Author: Anup Kumar Mondal (anuniqs@gmail.com) -->
<html>
  <head>
	<!-- no style -->
  </head>
  <body>
	<h1>Hello, World! Life is great!</h1>
  </body>
</html>
```

anup@megatron:~/hello$ git add lib/hello.html

anup@megatron:~/hello$ git commit -m 'Life is great!'

**02 View branches**

anup@megatron:~/hello$ git hist --all



### 28. Resolving Conflicts —

**01 Merge the master branch with style**

anup@megatron:~/hello$ git checkout style

anup@megatron:~/hello$ git merge master

anup@megatron:~/hello$ cat lib/hello.html

**02 Resolution of the conflict**

anup@megatron:~/hello$ nano lib/hello.html

```
<!-- Author: Anup Kumar Mondal (anuniqs@gmail.com) -->
<html>
  <head>
<<<<<<< HEAD
	<link type="text/css" rel="stylesheet" media="all" href="style.css" />
=======
	<!-- no style -->
>>>>>>> master
  </head>
  <body>
	<h1>Hello, World! Life is great!</h1>
  </body>
</html>
```

**To,**

```
<!-- Author: Anup Kumar Mondal (anuniqs@gmail.com) -->
<html>
  <head>
	<link type="text/css" rel="stylesheet" media="all" href="style.css" />
  </head>
  <body>
	<h1>Hello, World! Life is great!</h1>
  </body>
</html>
```

**03 Make a commit of conflict resolution**

anup@megatron:~/hello$ git add lib/hello.html

anup@megatron:~/hello$ git commit -m "Merged master fixed conflict."



### 29. Resetting the style branch —

**01 Resetting the style branch**

anup@megatron:~/hello$ git checkout style

anup@megatron:~/hello$ git hist

anup@megatron:~/hello$ git reset --hard 90ead67

**02 Check the branch**

anup@megatron:~/hello$ git hist --all



### 30. Reset of the Master branch —

**01 Resetting the master branch**

anup@megatron:~/hello$ git checkout master

anup@megatron:~/hello$ git hist

anup@megatron:~/hello$ git reset --hard 6d14fb1

anup@megatron:~/hello$ git hist --all



### 31. Rebase —

anup@megatron:~/hello$ git checkout style

anup@megatron:~/hello$ git rebase master

anup@megatron:~/hello$ git hist



### 32. Merging to the Master branch —

**01 Merging style into master**

anup@megatron:~/hello$ git checkout master

anup@megatron:~/hello$ git merge style

**02 Check the logs**

anup@megatron:~/hello$ git hist



### 33. Multiple repositories —

So far we have been working with only one git repository. However, git is great for working with several repositories. These additional repositories can be stored locally, or accessed via network connection.



### 34. Cloning repositories —

**02 Create a clone of the hello repository**

anup@megatron:~/hello$ cd

anup@megatron:~$ git clone hello cloned_hello

anup@megatron:~$ ls -ltr



### 35. Examine the cloned repository —

**01 Viewing the cloned repository**

anup@megatron:~$ cd cloned_hello/

anup@megatron:~/cloned_hello$ ls -ltr

**02 View the history of the cloned repository**

anup@megatron:~/cloned_hello$ git hist --all



### 36. What is origin? —

anup@megatron:~/cloned_hello$ git remote

anup@megatron:~/cloned_hello$ git remote -v

anup@megatron:~/cloned_hello$ git remote show origin


 
### 37. Remote branches —

**01 List of the remote branches**

anup@megatron:~/cloned_hello$ git branch

anup@megatron:~/cloned_hello$ git branch -a



### 38. Changing the original repository —

**01 Make a change in the original hello repository**

anup@megatron:~/cloned_hello$ cd ../hello/

anup@megatron:~/hello$ nano README

```
This is the Hello World example from the git tutorial.
(changed in original)
```

anup@megatron:~/hello$ git add README

anup@megatron:~/hello$ git commit -m "Changed README in original repo"


### 39. Fetching changes —

anup@megatron:~/hello$ cd ../cloned_hello

anup@megatron:~/cloned_hello$ git fetch

anup@megatron:~/cloned_hello$ git hist --all

anup@megatron:~/cloned_hello$ cat README



### 40. Merging pulled changes —

**01 Merge the pulled changes into the local master branch**

anup@megatron:~/cloned_hello$ git merge origin/master

anup@megatron:~/cloned_hello$ cat README



### 41. Pulling and merging changes —

git pull command is identical to git fetch plus git merge



### 42. Adding a tracking branch —

**01 Add a local branch tracking the remote branch.**

anup@megatron:~/cloned_hello$ git branch --track style origin/style

anup@megatron:~/cloned_hello$ git branch -a

anup@megatron:~/cloned_hello$ git hist --max-count=2


### 43. Bare repos —

**01 Creating a bare repository**

anup@megatron:~/cloned_hello$ cd ..

anup@megatron:~$ ls -ltr

anup@megatron:~$ git clone --bare hello hello.git

anup@megatron:~$ ls -ltr

anup@megatron:~$ ls -ltr hello.git/



### 44. Adding a remote repository —

anup@megatron:~$ cd hello

anup@megatron:~/hello$ git remote add shared ../hello.git



### 45. Submitting changes —

anup@megatron:~/hello$ nano README

```
This is the Hello World example from the git tutorial.
(Changed in the original and pushed to shared)
```

anup@megatron:~/hello$ git checkout master

anup@megatron:~/hello$ git add README

anup@megatron:~/hello$ git commit -m "Added shared comment to readme"

anup@megatron:~/hello$ git push shared master



### 46. Removing common changes —

anup@megatron:~/hello$ cd ../cloned_hello

anup@megatron:~/cloned_hello$ git remote add shared ../hello.git

anup@megatron:~/cloned_hello$ git branch --track shared master

anup@megatron:~/cloned_hello$ git pull shared master

anup@megatron:~/cloned_hello$ cat README



### 47. Placing your git repository —

**01 Run git server**
