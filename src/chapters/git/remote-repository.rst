Remote Repositories
===================

Local, Remote, GitHub, Oh My!
-----------------------------

So far, the book has covered how to setup a Git repository on the local machine, also known as **local development**.
One of the benefits of using a VCS is storage of backups in case something happens 
to your machine or you want to share your code with others.
Instead of keeping a Git repository only on a local machine, the code base is in a **remote repository**, 
allowing any programmers working on it keep copies on their local machine. 

We will be using GitHub to create our remote repositories.
You will need to create an account on `GitHub <https://www.github.com/>`_.
Make sure you choose an appropriate username.  Many programming professionals use GitHub as a portfolio for their work. 

Setting Up a Remote Repo
------------------------

Terminal and GitHub
^^^^^^^^^^^^^^^^^^^

Creating a repo from scratch on your own computer.

#. Create a folder on your computer to hold your codebase.  
#. ``cd`` into your folder and initialize it with git using the ``git init`` command.
#. Open GitHub and create a new repository.  
#. On the "Create a New Repository" page, name your repo the same as your folder so that you can stay organized better.
#. Keep it public for now
#. Don't check any boxes in the "**Initialize this repository with:**" section since we started this process on our computer.
#. Create the repository.
#. Select "**...or create a new repository in the command line**" option.  Copy the code and paste this into your terminal. Press the enter key.
   *Note:*  If you get a note from git to use a different command, type it into the terminal and hit enter.
#. Refresh your GitHub page and inspect your new repo.
#. Back on your computer, open your IDE and select the folder your repo is contained in and start coding.
#. Don't forget to save and commit your changes periodically.

Collaborating with Colleagues
-----------------------------

If a programmer wants to start collaborating with their colleagues on a new project, they might need to start with the work that one of their colleagues has already done.
In this particular case, the programmer has to import the work that is being stored in an online repository onto their local machine.

They can clone a remote repository by using the ``git clone url`` command.
Github and other online Git systems give users the option to clone the repository through HTTPS or SSH depending on how their Github profile is set up.
The ``url`` of the command is where the programmer adds the url to the repository that they are cloning. 

Cloning a Repo
^^^^^^^^^^^^^^

Using code from someone else's computer.

#. Create a folder on your computer to hold your codebase.
#. ``cd`` into your folder.
#. Open the repo that contains the codebase in GitHub.
#. Look for the button that says ``Code`` and click on it. 
#. On the dropdown menu, copy the link to the codebase.  In this class we will use the HTTPS code.
#. Back in your terminal, you will use the ``git clone`` command followed by the copied link. See example below:

   .. sourcecode:: bash

      Students-Computer:learning-git student$ git clone https://github.com:username/repo-name.git
#. Run the ``ls`` command to see what is now in your folder.
#. You will need to ``cd`` into the project folder in order to start coding.

Forking a Repo
^^^^^^^^^^^^^^

Creating a fork allows you to modify codebases without changing the original codebase.  
It is how you worked in replit.  And it is how you will gain access to any starter code in the remainder of this course.

#. Open the repo you wish to fork.
#. Locate the ``Fork`` button.  Currently is in the top right corner of a GitHub repo.
#. Click the ``Fork`` button.  If GitHub asks, make sure you save your fork into your class GitHub account.
#. A forked copy of the repo appear in GitHub.
#. You need to clone this fork onto your computer in order to work with its code. 

For more detailed instructions on how to fork, checkout out :ref:this walkthrough<forking>`.


.. admonition:: Fork or Clone?

   When working with LaunchCode GitHub repositories, you will want to fork the repository rather than clone it.


Contributing to a Remote Repository
-----------------------------------

Fork the ``learning-git`` `repo from GitHub <https://github.com/speudusa/learning-git>`_.

Open the repo you just forked in Visual Studio.  Explore it, run it.  See what happens. 
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

However, you updated the code.  
If you were working with a partner and they left that code commented out and built something else entirely, 
what would happen if they pushed up their changes?  A mess.  That is what. 


In the next section we will discuss how a way to avoid messes like that (in theory) by branching off the main branch.
A good practice for creating new features or working collaboratively or try new features without breaking your current code.

Check Your Understanding
------------------------------

.. admonition:: Question

   What is the new command for making a commit to a remote repository?
