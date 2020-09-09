# Git/GitHub Assignment

* **INDIVIDUAL ASSIGNMENT**
* **Deadline:** Sept-08
* **How to submit**: For each empty grey box, please provide with an answer to the item in a document. Do the following to *submit* the **Part 1** of your assignment:
1. Use the repo you created for Assignmen1 (*INF502*); 
2. create a file called *"Assignment2.md"* and paste your answers there (tip: click on *"Raw"* at the right-top of this file to get the markdown source); 

For **Part 2** the pull request created will the submission (except for item 4, which you need to add to the end of the Assignemnt1.md).

* **Value**: Part of homework grade

## Description
This assignment is composed of two parts. 
- [Part 1](#Part-1-Dealing-with-git) consists of executing a sequence of commands and giving explanations about the commands you have to run. 
For each item in the assignment, please provide appropriate explanation and/or the details requested.
- [Part 2](#Part-2-Using-GitHub) consists of creating a Markdown file on a fork of this course and creating a pull request towards this repo.

### Part 1: Dealing with git

To conduct this, you will have to download [handson.zip](handson.zip) and unzip it.
handson folder is a git repository. Using the command line change the directory to "handson/"

The empty boxes
```

```
represent the content you need to fill and post on your private repository


1. Describe what is the output of the following commands
    -  `git branch` 
    -  `git checkout BRANCH_NAME` (USE THE NAME OF AN EXISTING BRANCH)
    -  `git log --decorate`

```
1. git branch - We create branches so that we don't mess up with a running codebase. The branch created is a mirror image of the master code. Here in this code the output of the command shows two branches and the * denotes the branch I am currently working on and the other branch stays there.

$ git branch
* master
  math

2. git checkout BRANCH_NAME - This command is used to switch the branches. So in the command below I have switched to math branch and now the * sign is shown on math which means I am currently working on math.

$ git checkout math
Switched to branch 'math'
salon@DESKTOP-96N2GIK MINGW64 ~/OneDrive/INF502/handson (math)
$ git branch
  master
* math

3. git log --decorate - We see the log below of the activities performed with all the extra information. The current working branch is seen here i.e. math.

$ git log --decorate
commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:13:48 2019 -0700

    Adding some more knowledge to the function

commit 654b490a181dedf82dd6deda5f9848d6cca05918
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:12:14 2019 -0700

    Added a draft of A.py

commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:08:47 2019 -0700

     Creating all files (all empty)

```

2. Try `git log --graph --all`. What do you see?
```
git log --graph --all - This shows how my repository looks like in a graphical way. It shows the master and the branch below and they are not merged and so the master does not know about the branch.

$ git log --graph --all
* commit 18931d12a8be7cac049b73c6bc8136e9482f3371 (master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:15:28 2019 -0700
|
|     Making a small change here
|
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:13:48 2019 -0700
|
|       Adding some more knowledge to the function
|
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:12:14 2019 -0700
|
|     Added a draft of A.py
|
* commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Wed Aug 14 23:08:47 2019 -0700

       Creating all files (all empty)
:


```

3. Use `git diff BRANCH_NAME` to view the differences from a branch and the current branch.
   Summarize the difference from master to the other branch.

```
git diff BRANCH_NAME - Since I am working on the math branch I differentiated with the master. This basically shows changes in the commits , working tree, etc but I haven't made an specific changes it just shows the baic message. 

$ git diff master
diff --git a/A.py b/A.py
index dc1e9bd..0afa98c 100644
--- a/A.py
+++ b/A.py
@@ -1,3 +1,11 @@
 #this is just an example, do not freak out
 def calculate_this(operator, num1, num2):
-   print 'my knowledge is limited'
+   if operator == 'sum':
+      print num1 + num2
+      print 'That was easy buddy'
+   else:
+      if operator == 'subtraction':
+         print num1 - num2
+         print 'I could handle that...'
+      else:
+         print 'my knowledge is limited'
diff --git a/B.py b/B.py
index c63f94c..e69de29 100644
--- a/B.py
+++ b/B.py
@@ -1 +0,0 @@
-# Another file that will receive a line of code... at least.


```

4. Write a command sequence to merge the non-master branch into `master`

```
$ git merge math
Merge made by the 'recursive' strategy.
 A.py | 10 +++++++++-
 1 file changed, 9 insertions(+), 1 deletion(-)


```


5. Write a command (or sequence) to (i) create a new branch called `math` (from the `master`) 
and (ii) change to this branch (yes, `math` is already there, just report what you've done, the error and the reason you got the error. If you deleted and recreated the branch, you are fine too)

```
(i) $ git branch math
(ii) $ git checkout math

```
   
6. Edit B.py adding the following source code below the content you have there
```
print 'I know math, look:'
print 2+2
```
```
salon@DESKTOP-96N2GIK MINGW64 ~/OneDrive/INF502/handson (math)
$ vi B.py

salon@DESKTOP-96N2GIK MINGW64 ~/OneDrive/INF502/handson (math)
$ cat B.py
# Another file that will receive a line of code... at least.
print 'I know math, look:'
print 2+2

```
7. Write a command (or sequence) to commit your changes
```
$ git commit B.py -m "hello world"
[math 8d874ec] hello world
 1 file changed, 2 insertions(+)

```

8. Change back to the `master` branch and change B.py adding the following source code (commit your change to `master`):
```
I committed my change in math file first and then I came to execute the master files and this is the error I get
```

```
print 'hello world!'
```

```
$ git commit B.py -m "I know math"
warning: LF will be replaced by CRLF in B.py.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in B.py.
The file will have its original line endings in your working directory
[math 66d6ebf] I know math
 1 file changed, 2 insertions(+)
```

9. Write a command sequence to merge the `math` branch into `master` and describe what happened
```
$ git merge math
Auto-merging B.py
CONFLICT (content): Merge conflict in B.py
Automatic merge failed; fix conflicts and then commit the result.


```
   
10. Write a set of commands to abort the merge
```
$ git merge --abort

```
   
11. Now repeat item 9, but proceed with the manual merge (Editing B.py). All implemented functions are needed. Explain your procedure
```
-First, the master file is edited withg all the fi=unction in the B.py of math branch.

-Second, commit the file
$ git commit B.py -m "Manual merging"
[master 51c3ec1] Manual merging
 1 file changed, 2 insertions(+)

-Third, I see for the difference in the branches
$ git diff math
diff --git a/B.py b/B.py
index df01d77..8c72194 100644
--- a/B.py
+++ b/B.py
@@ -1,2 +1,4 @@
-print 'I know math,look:'
+# Another file that will receive a line of code... at least.
+print 'hello world!'
+print 'I know math, look:'
 print 2+2

-I check the status and see for the conflicts
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   B.py

no changes added to commit (use "git add" and/or "git commit -a")

salon@DESKTOP-96N2GIK MINGW64 ~/OneDrive/INF502/handson (master|MERGING)
$ git commit -a
[master f9def35] Merge branch 'math'

salon@DESKTOP-96N2GIK MINGW64 ~/OneDrive/INF502/handson (master)
$ cat b.py
<<<<<<< HEAD
# Another file that will receive a line of code... at least.
print 'hello world!'
print 'I know math, look:'
=======
print 'I know math,look:'
>>>>>>> math
print 2+2

-I added the file
$ git add B.py

salon@DESKTOP-96N2GIK MINGW64 ~/OneDrive/INF502/handson (master)
$ git status
On branch master
nothing to commit, working tree clean

```

12. Write a command (or set of commands) to proceed with the merge and make `master` branch up-to-date
```
$ git merge math
Already up to date.


```

### Part 2: Using GitHub

The goal of this assignment is to put you in touch with the fork-pullrequest process, with an extra of dealing a little bit with Markdown. To learn more about Markdown [click here](https://guides.github.com/features/mastering-markdown/).

**You must fork this repo and submit a pull request back**

1. Into the students folder, create a file called LASTNAME_FIRSTNAME.md (please change LASTNAME_FIRSTNAME for your actual last and first names). 
2. Use Markdown to structure the following information about the last paper you've read (you can structure your markdown the way you want):
- Title
- Venue (journal name/conference)
- Number of pages
- 3 outcomes of the paper
- link to the paper online

3. Send your file back to this repository until creating a pull request (your pull request needs to appear [here](https://github.com/igorsteinmacher/CS502-Fall2019/pulls)).

4. Report your experience of making this submission, including the steps followed, commands used, and hurdles faced (within the file you created for the **Part 1**.
```
It was a fun assignment. I faced issues in merging file as I am new to the command line but I could find my solutions to the issues on google and this has helped me understand git better.

```




 
