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

When working with a remote repository, you have a similar commit process as before.  Only now, you need to push your changes up to the remote repo
When working with a remote repo, the commit process has five steps:

1. ``git status``
2. ``git add``
3. ``git commit -m message-here``
4. ``git push origin main``
5. ``git log``

The fourth step uses the new command ``git push`` where the commit is pushed to the remote from the local.
``origin`` indicates that the commit does indeed go to the remote and ``main`` is the name of the branch that the commit goes to. 

Often when pushing to a remote repo you are commiting any changes that you made to the code. 
If you are the only one contributing to the codebase, then you are in control of what changes are being made.
However, it is not uncommon to share a codebase remotely with others.  
When working like this, it is not easy to manage and keep track of their changes and your own.
What happens when multiple people are adding to a single codebase?  You get a mess.

In the next section we will discuss how a way to avoid messes like that (in theory) by creating branches.
A good practice for creating new features or working collaboratively.

Check Your Understanding
------------------------------

.. admonition:: Question

   What is the new command for making a commit to a remote repository?
