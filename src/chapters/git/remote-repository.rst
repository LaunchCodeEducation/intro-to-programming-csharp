Remote Repositories
===================

Local, Remote, GitHub, Oh My!
-----------------------------

So far, the book has covered how to setup a Git repository on the local machine, also known as **local development**.
One of the benefits of using a VCS is storage of backups in case something happens 
to your machine or you want to share your code with others.
Instead of keeping a Git repository only on a local machine, the code base is in a **remote repository**, allowing any programmers working on it keep copies on their local machine. 

To get started with remote repositories, create an account on `GitHub <https://www.github.com/>`_.
From there, programmers can :ref:`create a remote repository<create-new-repo-demo>`, view commit history, and report issues with the code.

Collaborating with Colleagues
-----------------------------

If a programmer wants to start collaborating with their colleagues on a new project, they might need to start with the work that one of their colleagues has already done.
In this particular case, the programmer has to import the work that is being stored in an online repository onto their local machine.

They can clone a remote repository by using the ``git clone <url>`` command.
GitHub and other online Git systems give users the option to clone the repository through HTTPS or SSH depending on how their GitHub profile is set up.
The ``<url>`` of the command is where the programmer adds the url to the repository that they are cloning. 


.. note::

   Throughout this book, HTTPS will be used for cloning repositories.

   TOKEN NOW:  https://www.youtube.com/watch?v=kHkQnuYzwoo

In order to clone a repo, you will need to make a directory to store it.  Go ahead and create a ``learning-git`` repo.

::

   Students-Computer:~ student$ mkdir learning-git
   Students-Computer:~ student$ cd learning-git

Once you have the repo on your computer, ``clone this-repo<REPO GOES HERE>``.


::

   Students-Computer:learning-git student$ git clone <url-here>
   Cloning into 'learning-git'...
   remote: Enumerating objects: 13, done.
   remote: Counting objects: 100% (13/13), done.
   remote: Compressing objects: 100% (10/10), done.
   remote: Total 13 (delta 3), reused 13 (delta 3), pack-reused 0
   Receiving objects: 100% (13/13), 4.77 KiB | 4.77 MiB/s, done.
   Resolving deltas: 100% (3/3), done.
   Students-Computer:learning-git student$


.. admonition:: Fork or Clone?

   When working with LaunchCode GitHub repositories, 
   you will want to fork the repository rather than 
   clone it.

   Forking allows you to copy a project and modify it on a unique timeline.
   Meaning that, once forked then cloned, any changes you make will only affect this forked version.

   The :ref:`following guide<forking>` will help you with the forking process.

Contributing to a Remote Repository
-----------------------------------

Now that you have a profile on GitHub and a local copy of a remote repository, let's start coding!

Open the repo you just cloned in Visual Studio.  Explore it, run it.  See what happens. 
Go to the ``NumberChecks`` class and uncomment the ``EvenOrOddCheck`` method.  
Run it again to make sure it works. Then, save your project. 

.. index:: ! remote repository commit

.. index:: ! remote repository push

Now it is time to make a commit.
When working with a remote repo, the commit process has five steps:

1. ``git status``
2. ``git add``
3. ``git commit``
4. ``git push origin main``
5. ``git log``

The fourth step uses the new command ``git push`` where the commit is pushed to the remote from the local.
``origin`` indicates that the commit does indeed go to the remote and ``main`` is the name of the branch that the commit goes to. 

::

   Students-Computer:learning-git student$ git status
   On branch main
   Your branch is up to date with 'origin/main'.

   Changes not staged for commit:
   (use "git add <file>..." to update what will be committed)
   (use "git checkout -- <file>..." to discard changes in working directory)

         modified:   learning-git/NumberChecks.cs

   no changes added to commit (use "git add" and/or "git commit -a")
   Students-Computer:learning-git student$ git add .
   Students-Computer:learning-git student$ git commit -m "EvenOrOddCheck active"
   [main 72fb272] EvenOrOddCheck active
    1 file changed, 1 insertion(+)
   Students-Computer:learning-git student$ git push origin main
   Counting objects: 4, done.
   Delta compression using up to 4 threads.
   Compressing objects: 100% (4/4), done.
   Writing objects: 100% (4/4), 423 bytes | 423.00 KiB/s, done.
   Total 4 (delta 2), reused 0 (delta 0)
   remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
   To github.com:speudusa/learning-git.git
      3163e4b..72fb272  main -> main
   Students-Computer:learning-git student$ git log
   commit 72fb2723b02841469bdb54e129145181e28fc5a1 (HEAD -> main, origin/main)
   Author: Courtney Frey <cfrey@launchcode.org>
   Date:   Thu Jul 8 16:18:22 2021 -0500

      EvenOrOddCheck active



Great job!  

Now, you saw how easy it was to make changes to a repository and push them up.
Since you are the only one working on this repo as we walkthrough this process, 
you don't need to worry about interferring with the work of others.  

However, you uncommented a large amount of code.  
If you were working with a partner and they left that code commented out and built something else entirely, 
what would happen if they pushed up their changes?  A mess.  That is what. 


In the next section we will discuss how a way to avoid messes like that (in theory) by branching off the main branch.
A good practice for creating new features or working collaboratively or try new features without breaking your current code.

Check Your Understanding
------------------------------

.. admonition:: Question

   What is the new command for making a commit to a remote repository?
