Git Trees and Branches
======================

.. index:: ! branch

Branching in Git
----------------

So far this book has talked about Git's ability to store different versions of a code base in time.  
But what if you want to store different features of a code base in one place?  
What if you want collaborate with another programmer on separate features for the same code base?

This is another feature of using Git.  

Let's say you were working with a fellow programmer to create an app that tests if an number is even or odd.
Together you created a small app with a method that does just that.  Great!  
Later, you were asked to create another method to do something else with the number.

Before you get started coding, let's think about your current app.  It is functional.  
Do you know if your new feature will work right away or could there be any breakage?
That is not an easy question to answer.

* * * * * *

A great way to not have to worry about interfering with your currently functional code is to create a **branch**.
A branch is a separate version of the same code base.  
Like a branch on a tree, a branch in Git shares the same trunk as other branches, but is an individual.
Branches are great for storing and testing new features of software called **feature branches**.
Feature branches are great for working on a new feature without risking any potential failure or breakage of your main code base.

Another great feature of branches is collaboration between programmers.
With branches, two programmers could work on separate versions of the same code without interfering with each other's work.









In the previous section, when checking the status, the top line was ``On branch master``. 
The master branch is the *default branch* of the repository.
Many programmers keep the live version of their code in the master branch.
For that reason, major work should be done in a new branch, so it doesn't impact the live software.


     
   
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

.. _rename-branch:

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
