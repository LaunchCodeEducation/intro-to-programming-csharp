Remote Repositories
===================

Local, Remote, GitHub, Oh My!
-----------------------------

So far, the book has covered how to set up a Git repository on the local machine, 
also known as **local development**.
VCS is a great tool for backing up your codebase. 
VCS also allows you to share your code with others in  **remote repositories**.
Remote repositories are hosted on a server and accessible to others.

We will be using GitHub to create our remote repositories.
You will need to create an account on `GitHub <https://www.github.com/>`_.
Make sure you choose an appropriate username.  Many programming professionals use GitHub as a portfolio for their work. 

.. _remote-repo-setup:

Setting Up a Remote Repo
------------------------

Terminal and GitHub
^^^^^^^^^^^^^^^^^^^

Creating a repo from scratch on your own computer.

#. Create a folder on your computer to hold your codebase.  
#. ``cd`` into your folder and initialize it with git using the ``git init`` command.
#. Open your IDE and save all your work in your new directory.
#. ``commit`` your new project locally.
#. Open GitHub and create a new repository.  
#. On the "Create a New Repository" page, name your repo the same as your folder so that you can stay organized better.
#. Keep it public for now
#. Don't check any boxes in the "**Initialize this repository with:**" section since we started this process on our computer.
#. Create the repository.
#. Select "**...or push an existing repository from the command line**" option.  Copy the code and paste this into your terminal. 
   Press the enter key.
   *Note:*  If you get a note from git to use a different command, type it into the terminal and hit enter.
#. Refresh your GitHub page and inspect your new repo.
#. Back on your computer, open your IDE and select the folder that contains your repo and start coding.
#. Don't forget to save and commit your changes periodically.

Collaborating with Colleagues
-----------------------------

To start collaborating with their colleagues on a project, a programmer needs access to the codebase. 
The programmer has to import the code from a remote repository onto their local machine.

They can clone a remote repository by using the ``git clone url-here`` command.
Online VCSs, like GitHub, give users the option to clone the repository 
through HTTPS or SSH.
The ``url-here`` of the command is where the programmer adds the url to the repository that they are cloning. 

Cloning a Repo
^^^^^^^^^^^^^^

Using code from someone else's computer or repo.

#. Create a folder on your computer to hold your codebase.
#. ``cd`` into your folder.
#. Open the repo that contains the codebase in GitHub.
#. Look for the button that says ``Code`` and click on it. 
#. On the dropdown menu, copy the link to the codebase.  In this class, we will use the HTTPS code.
#. Back in your terminal, you will use the ``git clone`` command followed by the copied link. See the example below:

   .. sourcecode:: bash

      Students-Computer:learning-git student$ git clone https://github.com:username/repo-name.git
      
#. Run the ``ls`` command to see what is now in your folder.
#. You will need to ``cd`` into the project folder to start coding.

Forking a Repo
^^^^^^^^^^^^^^

Creating a fork allows you to modify codebases without changing the original codebase.  
It is how you worked in replit.  And it is how you will gain access to any starter code in the remainder of this course.

#. Open the repo you wish to fork.
#. Locate the ``Fork`` button.  Currently is in the top right corner of a GitHub repo.
#. Click the ``Fork`` button.  If GitHub asks, make sure you save your fork into your class GitHub account.
#. A forked copy of the repo appears in GitHub.
#. You need to clone this fork onto your computer to work with its code. 

For more detailed instructions on how to fork, checkout out :ref:this walkthrough<forking>`.


.. admonition:: Fork or Clone?

   When working with LaunchCode GitHub repositories, you will want to fork the repository rather than clone it.


Contributing to a Remote Repository
-----------------------------------

When working with a remote repository, you have a similar commit process as before. 
Now you need to push your changes up to the remote repo. 
When working with a remote repo, the commit process has five steps:

1. ``git status``
2. ``git add``
3. ``git commit -m message-here``
4. ``git push origin main``
5. ``git log``

The fourth step uses the new command ``git push...``.  
This pushes the commit to the remote from the local. ``origin`` indicates that the commit 
goes to the remote and ``main`` is the name of the branch that the commit goes to.

Often when pushing to a remote repo you are committing any changes that you made to the code. 
If you are the only one contributing to the codebase, then you are in control of what changes are being made.
Yet, it is not uncommon to share a codebase remotely with others.  
When working like this, it is not easy to manage and keep track of their changes and your own.
What happens when multiple people are adding to a single codebase?  You get a mess.

In the next section, we will discuss how a way to avoid messes like that (in theory) by creating branches.
A good practice for creating new features or working collaboratively.

Check Your Understanding
------------------------------

.. admonition:: Question

   What is the new command for making a commit to a remote repository?
