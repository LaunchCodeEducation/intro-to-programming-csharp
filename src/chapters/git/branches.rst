Branches
========

.. index:: ! branch

Branching in Git
----------------

So far this book has talked about Git's ability to store different versions of a code base.
What if two programmers want to work on different features of the code base at the same time?
What if you wanted to work together on creating a quiz, like you did for Assignment 1.
They may want to start with the same version and then one programmer wants to change the first and second questions and the other wants to have ten questions total.
It would not be effective for the two programmers to commit their changes to the repository at the same time.
Instead, Git has branches.
A **branch** is a separate version of the same code base.
Like a branch on a tree, a branch in Git shares the same trunk as other branches, but is an individual.
With branches, the two programmers could work on separate versions of the same website without interfering with each other's work.
Besides collaboration, programmers use branches for storing and testing new features of software called **feature branches**.

In the previous section, when checking the status, the top line was ``On branch master``. 
The master branch is the *default branch* of the repository.
Many programmers keep the live version of their code in the master branch.
For that reason, major work should be done in a new branch, so it doesn't impact the live software.

.. admonition:: Note

   **A note on** ``main`` **branch vs.** ``master`` **branch.**

   When you are using your terminal to create a repo on your own computer, you will often see
   the ``master`` branch. 
   
   If you push your repo into GitHub, you may see that your ``master`` branch is now called ``main``.  
   As of 2021, GitHub has renamed ``master`` as ``main``.  
   Older repos will still have a ``master`` branch, while newer repos will have a ``main`` branch.  
   Both ``master`` and ``main`` are the default branches for development and can be treated the same. 
   The command ``git branch`` can quickly help you see what the default branch is named and 
   let you decide what you want to do about it.  

   We will cover how to rename branches in this section.
     
   
.. figure:: figures/branches.png
   :alt: Diagram depicting two branches coming off of the main branch.

Checking on Your Branches
--------------------------

A quick way to check on your branches, whether to verify names or even a fast way to see which branch you are on 
is to use the command ``git branch``.  This will display a complete list of your branches.
There will also be some visual cue to let you know which branch you are on.  
This could be a unique color or an ``*``; it depends on the browser.  

Before you start coding, it can be a good idea to start by running a 
``git status`` or ``git branch`` to make sure you are in the right place.
Even if you haven't added any branches yet, you can still use this command.


.. admonition:: Example
   
   ::

      Students-Computer:~ student$ git branch
      * master
      Students-Computer:~ student$ git status
      On master branch


.. index:: ! creating new branch

Creating a New Branch
---------------------

A programmer is on master and they want to start building a new feature in a new branch.
Their first step would be to create a new branch for their work.

To create a branch, the command is ``git checkout -b <branch name>``.
By using this command, not only is a new branch created, but also the programmer switches to their new branch.

.. admonition:: Example

   Our program is going to be a quiz.  
   We want to add a new branch called ``quiz``.  
   This is the branch we will use to work on the questions.

   ::

      Students-Computer:~ student$ git branch
      * master
      Students-Computer:~ student$ git checkout -b quiz
      Switched to a new branch 'quiz'
      Students-Computer:~ student$ git branch
      master
      * quiz      

Switching to an Existing Branch
-------------------------------

If the branch already exists, the programmer may want to switch to that branch.
To do so, the command is ``git checkout <branch name>``.

.. admonition:: Example

   ::

      Students-Computer:~ student$ git status
      On branch quiz
      nothing to commit, working tree clean
      Students-Computer:~ student$ git checkout master
      Switched to branch 'master'
      Students-Computer:~ student$ git branch
      * master
      quiz     

Renaming a Branch
-------------------

Sometimes you might want to rename a branch.  You can do that in a few ways, with a few steps each.

.. admonition:: Example 

   Let's rename ``master`` to ``main``.

   **Option 1:** 
      - Checkout the branch you want to rename:  ``git checkout old-name``  
      - Use the following command: ``git branch -m new-name``

   ::
   
      Students-Computer:~ student$ git branch
      master
      * quiz
      Students-Computer:~ student$ git checkout master
      Students-Computer:~ student$ git status
      On master branch
      Students-Computer:~ student$ git branch -m main
      Students-Computer:~ student$ git branch
      * main
      quiz



Ta-da! Do quick branch check to verify your changes.  We'll walkthrough Option 2 using our newly named ``main`` branch.
Let's rename ``quiz`` to ``quiz-class``

.. admonition:: Example
   
   **Option 2:**  
      - Step 1: Checkout your ``main`` branch:  ``git checkout main``.
      - Step 2: You will then use the following command: ``git branch -m old-name new-name``

   ::

      Students-Computer:~ student$ git checkout main
      Students-Computer:~ student$ git status
      On main branch
      Students-Computer:~ student$ git branch -m quiz quiz-class
      Students-Computer:~ student$ git branch
      * main
      quiz-class

Remember, that names are up to you.  
Just like with commit messages, create branch names that will help you remember the branch's purpose.  

Check Your Understanding
------------------------

.. admonition:: Question

   What is a reason for creating a branch in Git?
