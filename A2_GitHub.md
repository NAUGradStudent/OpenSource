1. Create a new repository under your GitHub account called *OpenSource* (it may be private);
2. Create a file called *"A2_GitHub.md"*;
3. Copy the questions from this section and paste in your *"A2_GitHub.md"* file (tip: to copy the questions, click on *"Raw"* at the right-top of this file; this will show you the markdown source);
4. For each empty grey box, please provide an answer to the questions below.
5. Invite me to see your new repository. This will allow you to keep a private repository that only you and me will be able to see.



1. List all the branches in this repository and, for each branch, list the commits.

    - Use `git branch` to list the branches in this repository.
    
  
    - Use `git checkout` to explore each branch.
     
    - Use `git log --decorate` to explore the structure of commits.


```
-$ git branch
    
      feature-foo
      * master
      
    -$ git checkout feature_foo
    
    
    -$ git log --decorate
    
    commit a70a8e9d3c5390e367028faf033f2a9ef03d2e91 (HEAD -> feature-foo)
    Author: Igor Steinmacher <igorsteinmacher@gmail.com>
    Date:   Fri Aug 24 15:29:22 2018 -0700

    Adding header of method foo()

    commit 309b0d73ff9c2163591c9e96e307fe61b4c8f58a
    Author: Igor Steinmacher <igorsteinmacher@gmail.com>
    Date:   Fri Aug 24 15:27:16 2018 -0700

    Adding class A skeleton

    commit 9c1eeb8901b0926ce7fa13cc6ce0a1876fc4179b
    Author: Igor Steinmacher <igorsteinmacher@gmail.com>
    Date:   Fri Aug 24 15:26:44 2018 -0700

    Creating all files (all empty)


```

2. Try `git log --graph --all` to see the commit tree. Paste the result here and write a paragraph to provide an interpretation of what you found.
```
* commit f67f266cf420735187053f10d32e2c0f7cbc5a43 (master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Fri Aug 24 15:30:05 2018 -0700
|
|     Adding class B skeleton
|
| * commit a70a8e9d3c5390e367028faf033f2a9ef03d2e91 (HEAD -> feature-foo)
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Fri Aug 24 15:29:22 2018 -0700
|
|       Adding header of method foo()
|
* commit 309b0d73ff9c2163591c9e96e307fe61b4c8f58a
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Fri Aug 24 15:27:16 2018 -0700
|
|     Adding class A skeleton
|
* commit 9c1eeb8901b0926ce7fa13cc6ce0a1876fc4179b
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Fri Aug 24 15:26:44 2018 -0700

      Creating all files (all empty)


```

3. Choose an already existing branch and use `git diff BRANCH_NAME` to view the differences from a branch and the current branch. Summarize the difference from master to the other branch.

```
diff --git a/A.java b/A.java
index 3ea227e..674b8ce 100644
--- a/A.java
+++ b/A.java
@@ -1,4 +1,7 @@
 public class A {
-
+
+   public void foo() {
+
+   }

 }
diff --git a/B.java b/B.java
index ae64e6b..e69de29 100644
--- a/B.java
+++ b/B.java
@@ -1,4 +0,0 @@
-public class B {
-
-
-}


```

4. Write a command sequence to merge the branch that is not the master branch into `master`.

```

$ git merge new_branch
```


5. Write a command (or sequence) to (i) create a new branch called `math` (from the `master`) and (ii) change to this branch.

```
git checkout -b math master


```
   
6. Edit B.java adding the following source code below the content you have there.
```
public class B {
  public static void main(String[] args) {
    System.out.println("Hello from B");
    System.out.println("I know math, look:");
    System.out.println(2+2);
  }
}

```

7. Write a command (or sequence) to commit your changes.
```
pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (math)
$ git add .
warning: in the working copy of 'B.java', LF will be replaced by CRLF the next time Git touches it

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (math)
$ git commit -m "Update the file in math"
[math 1e7db9e] Update the file in math
 1 file changed, 7 insertions(+)


```

8. Change back to the `master` branch and change B.java adding the following source code (commit your change to `master`):
```
System.out.println("hello world!");

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master)
$ git add .

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master)
$  git commit -m "update file in master"
[master 8f09471] update file in master
 1 file changed, 1 insertion(+), 4 deletions(-)

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master)
$ cat B.java
System.out.println("hello world!");

```

9. Write a command sequence to merge the `math` branch into `master` and describe what happened.
```

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master)
$ git merge math
Auto-merging B.java
CONFLICT (content): Merge conflict in B.java
Automatic merge failed; fix conflicts and then commit the result.

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master|MERGING)
$ cat B.java
<<<<<<< HEAD
System.out.println("hello world!");
=======
public class B {
  public static void main(String[] args) {
    System.out.println("Hello from B");
    System.out.println("I know math, look:");
    System.out.println(2+2);
  }
}
>>>>>>> math

```
   
10. Write a set of commands to abort the merge.
```
pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master|MERGING)
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
        modified:   A.java

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   B.java


pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master|MERGING)
$ git merge --abort

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master)


```
   
11. Now repeat item 9, but proceed with the manual merge (editing B.java). All implemented methods are needed. Explain your procedure.
```
pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master)
$ git merge math
Auto-merging B.java
CONFLICT (content): Merge conflict in B.java
Automatic merge failed; fix conflicts and then commit the result.

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master|MERGING)
$ cat B.java
<<<<<<< HEAD
System.out.println("hello world!");
=======
public class B {
  public static void main(String[] args) {
    System.out.println("Hello from B");
    System.out.println("I know math, look:");
    System.out.println(2+2);
  }
}
>>>>>>> math
pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master|MERGING)
$ git add .

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master|MERGING)
$ git commit -m "Fixed the issues"
[master 2f75374] Fixed the issues

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master)
$ git ststrau
git: 'ststrau' is not a git command. See 'git --help'.

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master)
$ git status
On branch master
nothing to commit, working tree clean

pt355@CMP4948 MINGW64 ~/Desktop/cs499/handson (master)
$ cat B.java
System.out.println("hello world!");
public class B {
  public static void main(String[] args) {
    System.out.println("Hello from B");
    System.out.println("I know math, look:");
    System.out.println(2+2);
  }
}


```

12. Write a command (or set of commands) to proceed with the merge and make `master` branch up-to-date.
```
git status
git merge math

```

13. Complete Part 2. Then, come back here and answer the following:
Report your experience of submitting the Part 2. Please, include the steps you followed, the commands you used, and the hurdles you faced (within the file you created for the **Part 1**).
```
1. I first use fork to create a copy of CS499-OSS. 2. I created a file in the students folder and gave it the name usinf, which stands for my last name and first name. 3. I've included information regarding the paper I read, "THE CATHEDRAL AND BAZAAR," in that file. 4. After finishing, I committed the file. 5. I have made a "Pull Request" after committing.
