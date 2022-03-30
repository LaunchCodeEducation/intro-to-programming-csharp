Git Branches
============

.. index:: ! branch

Branching in Git
----------------

So far this book has talked about Git’s ability to store different versions of a codebase in time. 
What if you and a fellow programmer on separate features for the same codebase? 
What if you want to try something new in your code, but you don’t want to break your current code?
This is where **branches** can be useful.

A branch is a contained copy of the codebase.  
Any code written in a branch will not interfere with the original codebase. 
Many programmers use branches to fix bugs or add features to a codebase.  
Branches enable you to share work between programmers.  
They provide each programmer with code in their own branch, 
allowing more people to work on the code at once. 
Branches allow for changes to an already functional codebase.

In the previous section, when checking the status, the top line was ``On branch main``. 
The main branch is the *default branch* of the repository.  
Many programmers keep the live version of their code in the main branch.
For that reason, complete any major work in a new feature branch, so it doesn't impact the live software.

.. figure:: figures/branches-copy.png
   :alt: Diagram depicting two branches coming off of the main branch.

Checking on Your Branches
--------------------------

A quick way to check on your branches is to use the command ``git branch``.  
This will display a complete list of your branches.
There will also be some visual cues to let you know which branch you are on.  
This could be a unique color or an ``*``; it depends on the terminal.  

Before you start coding, run a 
``git status`` or ``git branch`` to make sure you are in the right place.
Even if you haven't added any branches yet, you can still use this command.

.. admonition:: Example
   
   ::

      Students-Computer:~ student$ git branch
      * main
      Students-Computer:~ student$ git status
      On main branch


.. index:: ! creating new branch

.. _new-branch:

Creating a New Branch
---------------------

You are on ``main`` and you want to start building a new feature in a new branch.
Your first step would be to create a new branch for your work.

To create a branch, the command is ``git checkout -b branch-name``.
By using this command, not only is a new branch created, but also you switch to the new branch.

.. sourcecode:: bash

   Students-Computer:~ student$ git checkout -b update-branch
   Students-Computer:~ student$ git branch
   main
   * update-branch   

Switching to an Existing Branch
-------------------------------

If the branch already exists, you may want to switch to that branch.
To do so, the command is ``git checkout branch-name``.  

.. admonition:: Example

   .. sourcecode:: bash

      Students-Computer:~ student$ git checkout main
      Students-Computer:~ student$ git branch
      * main
      update-branch      


.. _rename-branch:

Renaming a Branch
-------------------

Sometimes you might want to rename a branch.  You can do that in a few ways.
While we are currently on our ``main`` branch, let's rename ``update-branch`` to ``array-update``.

.. admonition:: Example  
   
   **Option 1 allows you to rename a branch from another branch.**
      
   - Step 1: If not on ``main``, checkout your ``main`` branch:  ``git checkout main``.
   - Step 2: You will then use the following command: ``git branch -m old-name new-name``

   ::

      Students-Computer:~ student$ git checkout main
      Students-Computer:~ student$ git branch
      * main
      update-branch
      Students-Computer:~ student$ git branch -m update-branch array-update
      Students-Computer:~ student$ git branch
      array-update
      * main


Ta-da! Do a quick branch check to verify your changes.  

.. admonition:: Example 

   **Option 2 renames a branch while on that branch.**

   - Step 1: Checkout the branch you want to rename:  ``git checkout old-name``  
   - Step 2: Use the following command: ``git branch -m new-name``

   ::
   
      Students-Computer:~ student$ git branch
      main
      * update-branch
      Students-Computer:~ student$ git branch -m pos-neg
      Students-Computer:~ student$ git branch
      * array-update
      main


Remember, that names are up to you.  
Create branch names that will help you remember the branch's purpose.  


Check Your Understanding
------------------------

.. admonition:: Question

   What is one reason for creating a branch in Git?
