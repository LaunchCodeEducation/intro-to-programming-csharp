Git Branches
============

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
Do you know if your new feature will work right away? Could there be any breakage?
Those are not easy questions to answer.

A great way to not have to worry about interfering with your currently functional code is to create a **branch**.
A branch is a separate version of the same code base.  
Like a branch on a tree, a branch in Git shares the same trunk as other branches, but is an individual.
Branches are great for storing and testing new features of software called **feature branches**.
Feature branches are great for working on a new feature without risking any potential failure or breakage of your main code base.

Another great feature of branches is collaboration between programmers.
With branches, two programmers could work on separate versions of the same code without interfering with each other's work.


In the previous section, when checking the status, the top line was ``On branch main``. 
The main branch is the *default branch* of the repository.  
Many programmers keep the live version of their code in the main branch.
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
Your first step would be to create a new branch for your work.

To create a branch, the command is ``git checkout -b <branch name>``.
By using this command, not only is a new branch created, but also you switch to the new branch.

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

If the branch already exists, you may want to switch to that branch.
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

.. admonition:: Warning!

   Sometimes when switching between branches, 
   you might see a lot of red squiggly lines underneath code you were confident worked when you 
   left your branch.  

   Give your IDE a few seconds to catch up and they should go away.  

.. _rename-branch:

Renaming a Branch
-------------------

Sometimes you might want to rename a branch.  You can do that in a few ways to do this.
While we are currently on our ``main`` branch, let's rename ``num-check`` to ``pos-neg``.

.. admonition:: Example  
   
   **Option 1 allows you to rename a branch from another branch.**
      
   - Step 1: If not on ``main``, checkout your ``main`` branch:  ``git checkout main``.
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


Ta-da! Do quick branch check to verify your changes.  

.. admonition:: Example 

   **Option 2 renames a branch while on that branch.**

   - Step 1: Checkout the branch you want to rename:  ``git checkout old-name``  
   - Step 2: Use the following command: ``git branch -m new-name``

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


Remember, that names are up to you.  
Just like with commit messages, create branch names that will help you remember the branch's purpose.  

Update Your Code
-----------------

Before we move on to the next topic, merging your branches together.  We are going to add some code to our demo project.
We are going to create two new branches.  
If you did not create a new branch called ``pos-neg`` by this point, go ahead and make one. 

.. _pos-neg-branch:

``pos-neg`` feature branch
^^^^^^^^^^^^^^^^^^^^^^^^^^

Starting on your new ``pos-neg`` branch, 
add the following code to your ``NumberChecks`` class below the ``EvenOrOddCheck`` method.

.. admonition:: Example

   In the ``NumberChecks`` class add the following:

   .. sourcecode:: csharp
      :lineno-start: 18

      public static void PositiveOrNegative (double num)
         {
               if(num < 0)
               {
                  Console.WriteLine("Your number is negative");
               }
         }

   
   
   In ``Program.cs`` add the following below the "EvenOrOddCheck" method call.

   .. sourcecode:: csharp
      :lineno-start: 15

      NumberChecks.PositiveOrNegative(inputNum);




Run the program to make sure it works.  Save your code. Then stage it for a commit.  
Do NOT push it at this moment.  We will work on that step in the studio.  


``dec-point`` feature branch
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Return to your ``main`` branch.  The code from your ``pos-neg`` branch won't be there and that's good.
In this branch we are going to add a method to check for a decimal point and nothing else.

Create a new branch called ``dec-point``.  On this branch you will add the following code:

In the ``NumberChecks`` class, add the following code below ``EvenOrOddCheck``:

.. _dec-point-branch:

.. admonition:: Example

   In the ``NumberChecks`` class add the following:

   .. sourcecode:: csharp
      :lineno-start: 18

      public static void ContainsDecimalPoint(string str, double num)
        {
            if (!str.Contains("."))
            {
                NumberChecks.EvenOrOddCheck(num);
            }
            else
            {
                Console.WriteLine("Your number contains a decimal point.");
            }
        }

   In ``Program.cs`` replace the "EvenOrOddCheck" method call with the following:

   .. sourcecode:: csharp
      :lineno-start: 15

      NumberChecks.ContainsDecimal(input, inputNum);

Make sure you test and run this before saving.  Once saved, stage and commit your work.
Again, do NOT push it at this time.  Return to the ``main`` branch.

Before we move on to the next section, let's run one more ``git branch`` to check on our new branches.

::

   Students-Computer:~ student$ git branch
   dec-point
   * main
   pos-neg


You have two new branches that both contain new code.  
While we worked on these branches, the ``main`` branch was left undisturbed.  
When we return to ``main``, we know that the basic code we started with still works.

When me made our branches, each branch contained all the code from where it was branched off.
In our case, we returned to the ``main`` branch to create ``pos-neg`` and ``dec-point``.  
So both ``pos-neg`` and ``dec-point`` started with the same code base originally in the ``main`` branch.
Each branch allowed us to create code in an environment isolated from the code base.
This keeps the code base safe and functional while you experiment with other code.

Our ``main`` branch is sparse comapred to our new branches, 
but the code on our ``main`` branch never broke while we worked on it.  
You also have two new methods that you know can work with your ``main`` branch code.  
If you have a live app, branches are great for making updates or 
fixing bugs without pulling your app down.


Now the question is, how do you get that new code into your ``main`` branch?

Check Your Understanding
------------------------

.. admonition:: Question

   What is a reason for creating a branch in Git?
