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

A great way to not have to worry about interfering with your currently functional code is to create a **branch**.
A branch is a separate version of the same code base.  
Like a branch on a tree, a branch in Git shares the same trunk as other branches, but is an individual.
Branches are great for storing and testing new features of software called **feature branches**.
Feature branches are great for working on a new feature without risking any potential failure or breakage of your main code base.

Another great feature of branches is collaboration between programmers.
With branches, two programmers could work on separate versions of the same code without interfering with each other's work.


In the previous section, when checking the status, the top line was ``On branch main``. 
The main branch is the *default branch* of the repository.  
Many programmers keep the live version of their code in the master branch.
For that reason, major work should be done in a new branch, so it doesn't impact the live software.

   
.. figure:: figures/branches.png
   :alt: Diagram depicting two branches coming off of the main branch.

Checking on Your Branches
--------------------------

A quick way to check on your branches is to use the command ``git branch``.  
This will display a complete list of your branches.
There will also be some visual cue to let you know which branch you are on.  
This could be a unique color or an ``*``; it depends on the terminal.  

Before you start coding, it can be a good idea to start by running a 
``git status`` or ``git branch`` to make sure you are in the right place.
Even if you haven't added any branches yet, you can still use this command.


.. admonition:: Example
   
   ::

      Students-Computer:~ student$ git branch
      * main
      Students-Computer:~ student$ git status
      On main branch


.. index:: ! creating new branch

Creating a New Branch
---------------------

You are on main and you want to start building a new feature in a new branch.
Your first step would be to create a new branch for their work.

To create a branch, the command is ``git checkout -b <branch name>``.
By using this command, not only is a new branch created, but also the programmer switches to their new branch.

.. admonition:: Example

   Using the ``learning-git`` project, let's create a branch to add a new feature that will determine if a number is positive or negative.  
   We want to add a new branch called ``num-check``.  
   This is the branch we will use to work on this.

   ::

      Students-Computer:~ student$ git branch
      * main
      Students-Computer:~ student$ git checkout -b num-check
      Switched to a new branch 'num-check'
      Students-Computer:~ student$ git branch
      main
      * num-check      

Switching to an Existing Branch
-------------------------------

If the branch already exists, the programmer may want to switch to that branch.
To do so, the command is ``git checkout <branch name>``.  Let's switch back to ``main`` real fast.

.. admonition:: Example

   ::

      Students-Computer:~ student$ git status
      On branch num-check
      nothing to commit, working tree clean
      Students-Computer:~ student$ git checkout main
      Switched to branch 'main'
      Students-Computer:~ student$ git branch
      * main
      num-check     

.. _rename-branch:

Renaming a Branch
-------------------

Sometimes you might want to rename a branch.  You can do that in a few ways, with a few steps each.

.. admonition:: Example 

   Let's rename ``num-check`` to ``pos-neg`` to remind us what the purpose of this branch is.

   **Option 1:** 
      - Checkout the branch you want to rename:  ``git checkout old-name``  
      - Use the following command: ``git branch -m new-name``

   ::
   
      Students-Computer:~ student$ git branch
      main
      * num-check
      Students-Computer:~ student$ git checkout num-check
      Students-Computer:~ student$ git status
      On num-check branch
      Students-Computer:~ student$ git branch -m pos-neg
      Students-Computer:~ student$ git branch
      main
      * pos-neg



Ta-da! Do quick branch check to verify your changes.  

.. admonition:: Example

   Option 2 renames a branch while on a different branch.
   
   **Option 2:**  
      - Step 1: Checkout your ``main`` branch:  ``git checkout main``.
      - Step 2: You will then use the following command: ``git branch -m old-name new-name``

   ::

      Students-Computer:~ student$ git checkout main
      Students-Computer:~ student$ git branch
      * main
      num-check
      Students-Computer:~ student$ git branch -m num-check pos-neg
      Students-Computer:~ student$ git branch
      * main
      pos-neg

Remember, that names are up to you.  
Just like with commit messages, create branch names that will help you remember the branch's purpose.  

Update Your Code
-----------------

Before we move on to the next topic, merging your branches together.  We are going to add some code to our demo project.
We are going to create two new branches.  

``pos-neg`` branch
^^^^^^^^^^^^^^^^^^^

Starting on your new ``pos-neg`` branch add the following code to your ``NumberChecks class`` below the ``EvenOrOddCheck`` method.

.. sourcecode:: csharp

   //In the NumberChecks
   public static void PositiveOrNegative (double num)
        {
            if(num < 0)
            {
                Console.WriteLine("Your number is negative");
            }
        }

   //In the Program.cs you will need to call your new "PositiveOrNegative" method




Run the program to make sure it works.  Save your code. Then stage it for a commit.  
Do not push it at this moment.  We will work on that step in the studio.  

``dec-point`` branch
^^^^^^^^^^^^^^^^^^^^^

Return to your ``main`` branch.  The code from your ``pos-neg`` branch won't be there and that's good.
In this branch we are going to add a method to check for a decimal point.

In the ``NumberChecks`` class, add the following code below ``EvenOrOddCheck``:

.. sourcecode:: csharp

   //In the NumberChecks
   public static void ContainsDecimal(string stringNum)
        { 
            if (stringNum.Contains("."))
            {
                Console.WriteLine("Your number contains a decimal point.");
            }
        }

        //In the Program.cs you will need to call your new "ContainsDecimal" method

Make sure you test and run this before saving.  Once saved, stage and commit your work.
Again, don't push it at this time.  Return to the ``main`` branch.

Before we move on to the next section, let's run one more ``git branch`` to check on our new branches.

::

   Students-Computer:~ student$ git branch
   dec-point
   * main
   pos-neg


Check Your Understanding
------------------------

.. admonition:: Question

   What is a reason for creating a branch in Git?
