Merging in Git
==============
.. index:: ! merge, ! merge conflict, ! stash


A **merge** in Git is when the code in two branches are combined in the repository.
When merging you need to be on the branch you want to merge INTO.  

If we wanted to merge a branch that had a new feature into the ``main`` branch, 
the first step would be to checkout the ``main`` branch.

.. sourcecode:: bash

   Students-Computer:~ student$ git checkout main
 


While on the ``main`` branch, the command would be ``git merge feature-branch``.
This will combine the two branches by pulling our code from ``feature-branch`` into ``main``. 


Anything built on the ``feature-branch`` branch will now be incorporated into ``main``.
Git will provide output that indicates any changes that the ``feature-branch`` merged into the ``main`` branch.
Once your merge is complete, commit your work.

.. admonition:: Tip

   Before running the merge command, the programmer should make sure they are on the branch they want to merge into!

Merge Conflicts
---------------

Merging branchers is often seamless.  Sometimes we run into **merge conflicts**.  
A merge conflicts occur when a previously existing line of code was altered between two branches.
Git raises a conflict when it is not sure which code you actually want to keep.  
It is waiting for a human to review the issue and decide.

Merge Conflict Symbols 
^^^^^^^^^^^^^^^^^^^^^^^

Your IDE uses symbols to let you know where a conflict is located as well as show you which branch is responsible for which code.

Some terms and symbols to pay attention to when conflict arrises.

In Your Terminal:
   Git will be the first warning.  ``CONFLICT`` will appear in your git output.  Usually followed by a location for the error.

 
In Your IDE:
   #. ``<<<<<<<`` or ``<<<<<<< HEAD`` will appear at the first line of code where a conflict has been found.
      ``HEAD`` points to the current branch you are on, or the current changes.  Some IDEs will use the branch name instead of ``HEAD``.
   #.  ``=======`` will be the dividing line between the ``HEAD`` branch and the incoming branch.
   #. ``>>>>>>>`` or ``>>>>>>> branch-name`` contains code from the incoming branch to merge in. Often this notation will be found below the last line of code.
      This code may also be referred to as the incoming changes. 

When a conflict arrives, you get to decide which code you want to keep.  Do you want the incoming changes, do you want the current code? 
You get to decide.  

Merge conflicts are minor on small applications, but can cause issues with large enterprise applications.
Even though the thought of ruining software can be scary, every programmer deals with a merge conflict during their career.
The best way to deal with a merge conflict is to face it head on and rely on teammates for support!

Ways to Avoid Merge Conflicts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Even though merge conflicts are normal in Git, it is also normal for 
programmers to want to do everything they can to avoid them.
Here are some tips on how to avoid a merge conflict:

#. Git has a dry-run option for many commands.
   When a programmer uses that option, Git outputs what WILL happen, but doesn't DO it.
   With merging in Git, the command to run a dry-run and make sure there aren't any conflicts is ``git merge --no-commit --no-ff <branch>``.
   ``--no-commit`` and ``--no-ff`` tell Git to run the merge without committing the result to the repository.
#. Before merging in a branch, any uncommitted work that would cause a conflict needs to be dealt with.
   A programmer can opt to not commit that work and instead **stash** it.
   By using the ``git stash`` command, the uncommitted work is saved in the stash and the repository is returned to the state at the last commit.

Check Your Understanding
------------------------

.. admonition:: Question

   If a programmer is currently on a branch called ``quiz`` and wants to merge a branch called 
   ``feature`` into ``main``, what steps should they take?
