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
The master branch is the default branch of the repository.
Many programmers keep the live version of their code in the master branch.
For that reason, major work should be done in a new branch, so it doesn't impact the live software.

.. admonition:: Note

   GitHub is currently transitioning the name ``master`` to ``main``.  
   Older repos will still have a ``master`` branch, while newer repos will have a ``main`` branch.  
   Both ``master`` and ``main`` are the default branches for development and can be treated the same.  
     
   While you use this textbook, you may notice that your repos use ``main`` while the examples use ``master``.
   This is intentional.  As of this writing, the change in language is only with GitHub repositories.  Bash and Powershell still use ``master``. 
   You can read more about this in the `GitHub documentation <https://docs.github.com/en/github/getting-started-with-github/github-glossary#main>`_.

.. figure:: figures/branches.png
   :alt: Diagram depicting two branches coming off of the main branch.


Creating a New Branch
---------------------

A programmer is on master and they want to start building a new feature in a new branch.
Their first step would be to create a new branch for their work.

To create a branch, the command is ``git checkout -b <branch name>``.
By using this command, not only is a new branch created, but also the programmer switches to their new branch.

Switching to an Existing Branch
-------------------------------

If the branch already exists, the programmer may want to switch to that branch.
To do so, the command is ``git checkout <branch name>``.

Check Your Understanding
------------------------

.. admonition:: Question

   What is a reason for creating a branch in Git?
