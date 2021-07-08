Merging in Git
==============

.. index:: ! merge, ! merge conflict, ! stash

How to Merge
------------

A **merge** in Git is when the code in two branches are combined in the repository.
The command to merge a branch called ``quiz-class`` into ``main``.  
You need to be on the branch you want to merge *into*.  
Using our example, we would ``git checkout main`` and then ``git merge quiz-class``.  
This will combine the two branches by pulling our code from ``quiz-class`` into ``main``.  
Anything we build in the ``quiz-class`` branch will now be incorporated into ``main``.

.. admonition:: Tip

   Before running the merge command, the programmer should make sure they are on the branch they want to merge into!


If all goes to plan, you will ``git merge [whatever branch]`` and the two branches will not have any conflicts.
But that is not always the case.

Merge Conflicts
---------------

Merging branchers is often seamless.  Sometimes we run into **merge conflicts**.  
A merge conflicts occur when a previously existing line of code was altered between two branches.

Let's say in our ``main`` branch we initially started with an array of questions, answers, and user answers.
Arrays hold the questions, answers, and user's answers.  As the user works through the questions and provides their answers, 
they are graded on correctness and their final score is printed.  (Sound familiar?  Hello, Assignment 1).

However, as a challegne you wanted a way to easily add more questions and their corresponding correct answers. 
You created a new branch ``quiz-class`` to work on this possiblitiy.  As you worked, you changed the array into a List.

You've been working hard on in the ``quiz-class`` branch.  
You have staged, added, and committed your latest code.  You are ready to merge it into your main branch for deployment.

You ``git checkout main`` then ``git merge quiz-class``.  Your terminal looks like it's working then suddenly you see:


::
  
   CONFLICT (content): Merge conflict in YOUR-FILE-NAME-HERE/Program.cs
   Automatic merge failed; fix  conflicts and then commit the results.
   Students-Computer:~ student$ 

It might sound like a bad thing.  It is yelling "CONFLICT" at you afterall, but you can handle this.
What is really happening is that previously existing code has been altered in such a way that Git doesn't know
which version is the one you want to keep.  Now it is up to you to decided which code to keep and which to discard.
The best to start is to look at any specific files that were noted by Git.  In this case, we should look at the 
Program.cs file.

Merge Conflict Symbols 
^^^^^^^^^^^^^^^^^^^^^^^

Visual Studio uses the following symbols in a conflict.  
The visual output may vary between Mac and Windows; however, the same symbols and terms are used.
There are a lot of areas of conflict between our branches since we changed from array to List, but 
we are going to focus on this small example.

::

   <<<<<<< HEAD
            for (int i = 0; i <= questions.Length - 1; i++)
   =======
            for (int i = 0; i <= questions.Count - 1; i++)
   >>>>>>> quiz-class

The term ``HEAD`` is pointing to the branch you are merging *into* or your *current* branch.
So the notation ``<<<<<<< HEAD`` tells us that any code contained within this notation and ``=======`` is what is 
in the current branch (or HEAD branch).
The code found between the ``=======`` and ``>>>>>>> quiz-class`` is part of the incoming branch, 
or the branch we want to merge in.

When they are in conflict, you get to decided which lines you want to keep.
Each IDE has its own way to take the ``HEAD`` (current) version or ``quiz-class`` (incoming) version.
Once you are happy with the resolved conflict, save, stage, add, and commit your branch.

::

   [main 33975bb] conflicts resolved

This is cause for celebration!  

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

   If a programmer is on the branch ``quiz-class`` and wants to merge a branch called 
   ``feature`` into ``main``, what steps should they take?
