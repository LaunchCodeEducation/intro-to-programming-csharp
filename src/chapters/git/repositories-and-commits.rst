Repositories and Commits
=========================

.. index:: ! repository 

.. index:: ! repo

.. _create-repo:

Create a Repository
-------------------

To get started with a git repository (or "repo" for short), the programmer must first create one.
Let's walkthrough the steps together using the terminal and a text editor.

To create a git repository, you will need to navigate to your project directory using the terminal.
Either select a current directory or make one.  Let's make one called ``homework``.
Once created and you are inside your project directory, we are going to initiate git.

Go ahead and use the command ``git init``, like so:

.. sourcecode:: bash

   Students-Computer:~ student$ mkdir homework
   Students-Computer:~ student$ cd homework
   Students-Computer:homework student$ git init
      Initialized empty Git repository in /Users/student/homework/.git/

Congrats! You have initialized git version control in this directory.
Now you are ready to code away!

.. index:: ! git commit

Let's add some code or files to this project.  
Since we are using the terminal, let's create a text file by using ``touch my_project.txt``.  
Once that is done, open your new file, type your name, and save your file.

Back in your terminal, type ``git status``.

::

   Students-Computer:homework student$ git status
   On main branch

   No commits yet

   Untracked files:
      (use "git add <file>..." to include wht will be committed)

         my_project.txt
   
   nothing added to commit but untracked files present (use "git add" to track)
   Students-Computer:homework student$

Wow!  That's a lot of text for your new file.  
You saved your project on your computer, but let's commit it to your Git.  

.. _rename-branch:

.. admonition:: Note

   **A note on the** ``default`` **branch** 

   When using a VCS, the first branch created is your ``default`` branch.  
   On your computer, it is often named the ``master`` branch.  
   Later we will be working with GitHub, which is an online repository that is commonly used when collabotating with others.
   GitHub's default branch is called ``main``.  

   The examples in this chapter will be using ``main`` as the default branch.
   

   If you would like to :ref:`rename your branch<rename-branch>` to match, the git command is ``git branch -m NEW-NAME-HERE``.

   ::

      Students-Computer:~ student$ git branch -m main
      Students-Computer:~ student$ git status
      On branch main




Making Commits
--------------

Usually, you will have spent more time coding and saving, and will have a larger amount of code to stage and commit. 
For the sake of our walkthrough, we are going to keep things shorter and simpler.

Earlier we added our first file, ``my_project.txt``, to our ``homework`` directory.  It might be a good time to make a **commit** to your repository.  
A commit is a record of changes you made to your repository.
It allows you to document your progress by creating a time-stamp with a message that you, or others, can reference.
When you look at a timeline of commits, you should be able to see the progress of development.

.. figure:: figures/git_commit_2x.png
   :scale: 50%
   :alt: Image of commit tree showing a degression in commit messages as project drags on.
   
   Comic Source: `XKCD.com <https://xkcd.com/1296/>`_.  Used with permission.

So when do you make a commit to your repository?

.. pull-quote::

   The general rule of thumb is that any time a significant change in functionality is made, a commit should be made.

If you have created the Git repository and are ready to commit, you can do so by following the commit process.

.. note::

   Git does have a simple commit command, however, making a proper commit requires that you follow a longer procedure than just one command.

.. index:: ! stages of a commit

The Four Stages of Making a ``commit`` 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The procedure for making a commit to a Git repository includes four stages.  

#. ``git status`` gives you information about files that have been changed.
#. ``git add`` allows you to add specific or all changed files to a commit.
#. ``git commit -m MESSAGE`` creates the new commit with the files that you added, 
   with a message describing the changes included in the commit. Here, ``MESSAGE`` should be a descriptive message within double-quotes.
#. ``git log`` displays a log of every commit in the repository.

If the steps above are followed correctly, you will find your latest commit at the top of the log.

Here is how the process will look in the terminal:

::

   Students-Computer:homework student$ git status
   On main branch

   No commits yet

   Untracked files:
      (use "git add <file>..." to include what will be committed)

         my_project.txt
   
   nothing added to commit but untracked files present (use "git add" to track)
   Students-Computer:homework student$ git add my_project.txt
   Students-Computer:homework student$ git commit -m "My initial commit"
   [main (root-commit) 7e771d7] My initial commit
      1 file changed, 1 insertion (+)
      create mode 100644 my_project.txt
   Students-Computer:homework student$ git log
   commit 7e771d788ddfd6080f0a9f10f9aed7105b1a3bcf (HEAD -> main)
   Author: Student <lc101.student@email.com>
   Date:  Wed Apr 24 14:36:53 2019 -0500


That is even more text in your terminal.  
What it all comes down to is that you added your file with the ``git add`` command, 
then committed it to your repo using ``git commit -m "...message here..."``.  
This commit created a time stamp of your work.  You changed 1 file, by inserting 1 item.
Your changes will vary based on how much you add and save before committing.
We called ``git log`` to view the a time stamp of the commit.

That was a lot very fast.  Let's add one more file for practice and look at each step more closely.

In your terminal, create a second file, ``notes.txt`` using the ``touch`` command. 
Open that up, and write yourself another note.  Save your changes.  
Also, make changes in your ``my_project.txt`` file and save those changes.
Return to your terminal.

Let's go through the four steps to commit our repo.  
Once you get to step four, ``git log``, you should get a printout that looks similar to this:

::

   Students-Computer:~ student$ git status
      On branch main
      Your branch is up to date with 'origin/main'.

      Changes note staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git checkout -- <file>..." to discard changes in working directory)

        modified: my_project.txt

      Untracked files:
        (use "git add <file>..." to update what will be committed)

        notes.txt

      no changes added to commit (use "git add" and/or "git commit -a")
   Students-Computer:homework student$ git add my_project.txt
   Students-Computer:homework student$ git add notes.txt
   Students-Computer:homework student$ git commit -m "notes added to project"
    [main (root-commit) 2c1e0af] notes added to project
     2 file changed, 4 insertion(+), 1 deletion(-)
     create mode 100644 notes.txt
   Students-Computer:homework student$ git log
   commit 2c1e0af9467217d76c7e3c48bcf9389ceaa4714b (HEAD -> master)
   Author: Student <lc101.student@email.com>
   Date:  Wed Apr 24 14:44:59 2019 -0500

      notes added to project

To break down what happens in a commit even further, we will examine each step for 
meaning and the code.

.. index:: ! git status

When using ``git status``, the output shows two categories: **modified tracked files** and **modified untracked files**.
Modified tracked means that the file exists in the Git repository already, but is different than the version in the repository.
Modified untracked means that it is a new file that is not currently in the repository.

In the code block below, the ``my_project.txt`` is an example of a modified tracked file because we added to it before committing. 
``notes.txt`` is an example of a modified untracked file because it is brand new and has not been previously committed.

::

      Students-Computer:~ student$ git status
      On branch main

      Changes note staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git checkout -- <file>..." to discard changes in working directory)

        modified: my_project.txt

      Untracked files:
        (use "git add <file>..." to update what will be committed)

        notes.txt

      no changes added to commit (use "git add" and/or "git commit -a")
      Students-Computer:~ student$

.. index:: ! git add

``git add`` adds files to the commit, but it does not commit those files.
By using ``git add .``, *all* the modified files were added to the commit.
If a programmer only wants to add one modified file, they can do so.

::

   Students-Computer:homework student$ git add notes.txt
   Students-Computer:homework student$


Now, if we were to run a ``git status`` following our ``git add`` we would see the
following updates have been made.

::

   Students-Computer:homework student$ git status
   On main branch

   Changes to be committed:
      (use "git reset HEAD <file>..." to unstage)

      modified: my_project.txt
      new file: notes.txt
   
   Students-Computer:homework student$


.. index:: ! git commit

``git commit`` actually commits the files that were added to the repository.
By adding ``-m "notes added to project"``, a comment was added to the commit.
This is helpful for looking through the log and seeing detailed comments of the changes made in each commit.

::

   Students-Computer:homework student$ git commit -m "notes added to project"
    [main (root-commit) 2c1e0af] notes added to project
     2 file changed, 4 insertion(+), 1 deletion (-)
     create mode 100644 notes.txt
   
   Students-Computer:homework student$

.. admonition:: Tip

   It's important to include a descriptive commit message. Such messages are visible in your local Git log, as well as in the commit history on GitHub. A good commit message allows you and your fellow developers to easily identify the changes made in a given commit.

.. index:: ! git log

``git log`` shows the author of the commit, the date made, the comment, and a 40-character hash.
This hash or value is a key for Git to refer to the version.
Programmers use these hashes to reference specific commits, or snapshots, in the repository's history.

::

   Students-Computer:homework student$ git log
   commit 2c1e0af9467217d76c7e3c48bcf9389ceaa4714b (HEAD -> master)
   Author: Student <lc101.student@email.com>
   Date:  Wed Apr 24 14:44:59 2019 -0500

      notes added to project

   Students-Computer:homework student$

And if you were to run a final ``git status`` (your git best friend), you will see output similar to this:

::

      Students-Computer:homework student$ git status
      On branch main
      nothing to commit, working tree clean

This lets you know that you have committed all of your latest changes.  Great job!

.. admonition:: Tip

   If your terminal is getting too crowded for you, the command ``clear`` 
   will clear all lines in your terminal.  After this command runs, your cursor will be at the top of the terminal window.

Check Your Understanding
------------------------

.. admonition:: Question

   What git command is NOT a part of the commit process?

   #. ``git add``
   #. ``git log``
   #. ``git status``
   #. ``git push``
