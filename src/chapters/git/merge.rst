Merging in Git
==============

.. index:: ! merge, ! merge conflict, ! stash

How to Merge
------------

A **merge** in Git is when the code in two branches are combined in the repository.
When merging you need to be on the branch you want to merge INTO.  
If we wanted to merge ``pos-neg`` into the ``main`` branch, 
the first step would be to checkout the ``main`` branch.

::

   Students-Computer:~ student$ git checkout main
   Students-Computer:~ student$ git status
   On branch main
   nothing to commit, working tree clean



While on the ``main`` branch, the command would be ``git merge pos-neg``.
This will combine the two branches by pulling our code from ``pos-neg`` into ``main``. 
Anything we build on the ``pos-neg`` branch will now be incorporated into ``main``.


::

   Students-Computer:~ student$ git merge pos-neg
   Updating 61f4faf...d7a6ef6
   Fast-forward
      learning-git/NumberChecks.cs | 8 +++++++-
      learning-git/Program.cs 1 | +
      2 files changed, 8 insertions (+), 1 deletion (-)
   Students-Computer:~ student$

The specific numbers in our your output may vary based on any changes you made in your code, 
so don't worry if you have differences in your insertions or deletions.  
The key here is to look at which files were changed and that your merge was successful.  
Once merged, stage and commit your ``main`` branch.

.. admonition:: Tip

   Before running the merge command, the programmer should make sure they are on the branch they want to merge into!

If all goes to plan, you will ``git merge [whatever branch]`` and the two branches will not have any conflicts.
But that is not always the case.

Merge Conflicts
---------------

Merging branchers is often seamless.  Sometimes we run into **merge conflicts**.  
A merge conflicts occur when a previously existing line of code was altered between two branches.
Git raises a conflict when it is not sure which code you actually want to keep.  
It is waiting for a human to review the issue and decide.

Let's see this in action when we merge our ``dec-point`` branch into ``main``.

::
  
   Students-Computer:~ student$ git status
    On branch main
    nothing to commit, working tree clean
   Students-Computer:~ student$ git merge dec-point
   Auto-merging learning-git/Programs.cs
   CONFLICT (content): Merge comflict in learning-git/Program.cs
   Auto-merging learning-git/NumberChecks.cs
   CONFLICT (content): Merge conflict in learning-git/NumbersCheck.cs
   Automatic merge failed; fix conflicts and commit the result.

  
Well that didn't really go as planned.
Luckily, Git has detailed messages that will guide us to where the issues are in your program.
In this case, we have issues in our Program.cs file and our NumbersCheck.cs class.
Pair these Git message with your IDE, and you will be able to find the issues relatively quickly.

Let's look at our code and see if we can figure out where things went awry.

Merge Conflict Symbols 
^^^^^^^^^^^^^^^^^^^^^^^

Visual Studio uses the following symbols in a conflict.  
The visual output may vary between Mac and Windows; however, the same symbols are used.
There are a few of areas of conflict between our branches since we are trying to add a new method into the ``main`` branch.

Let's start with our NumberChecks class.

::

   <<<<<<< HEAD
        public static void PositiveOrNegative (double num)
        {
            if(num < 0)
            {
                Console.WriteLine("Your number is negative.");
   =======
        public static void ContainsDecimalPoint(string str, double num)
        {
            if (!str.Contains("."))
            {
                NumberChecks.EvenOrOddCheck(num);
            }
            else
            {
                Console.WriteLine("Your number contains a decimal point.");
   >>>>>>> dec-point
            }
        }


The term ``HEAD`` is pointing to the current branch. Which happens to be the one you are merging into at the moment.
So the notation ``<<<<<<< HEAD`` tells us that any code contained within this notation and ``=======`` is what is 
in the current branch (or HEAD branch).
The code found between the ``=======`` and ``>>>>>>> dec-point`` is part of the incoming branch, 
or the branch we want to merge in.

When they are in conflict, you get to decided which lines you want to keep.
Each IDE has its own way to take the ``HEAD`` (current) version, ``dec-point`` (incoming) version or both versions.

Let's look at our code and think about what changes we want to keep.
We want to merge in dec-point, so what is dec-point doing that we like and how can we incorporate it into our code?

Notice where the ``=======`` starts.  
We seem to be in the middle of the ``PositiveOrNegative`` method.  Count your ``{ }`` to check and see. 

A simple way to fix this particular conflict would be to adjust the code inside the conflict markers.

Within the ``<<<<<<< HEAD`` close the ``if`` statement and the method, by typing the closing ``}`` for each.
If you look at the ``ContainsDecimal`` method, you will see that the ``else`` statement and the entire method are
also missing the ``}``.  Go ahead and add those within the ``=======`` to ``>>>>>>> dec-point`` section.

Finally, remove the two ``}`` right below ``>>>>>>> dec-point``.
Should look like this when you are done:

.. sourcecode:: csharp

   <<<<<<< HEAD
        public static void PositiveOrNegative(double num)
        {
            if (num < 0)
            {
                Console.WriteLine("Your number is negative.");
            }
        }
   =======
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
   >>>>>>> dec-point

We now have two properly formatted methods. Fantastic! 
Now we need to decide how which changes to keep.  
In this instance, select ``Accept Both`` or ``Take both``.
Now the ``NumberChecks`` class has three separate methods.  All have the correct number of brackets.

If we go back to the ``Program.cs`` file, we still have a conflict waiting for us.

.. sourcecode:: csharp

   <<<<<<< HEAD
            NumberChecks.EvenOrOddCheck(inputNum);
            NumberChecks.PositiveOrNegative(inputNum);
   =======
            NumberChecks.ContainsDecimalPoint(input, inputNum);
   >>>>>>> dec-point

We are calling all of the methods.  We don't need all three.
If you remember the  ``ContainsDecimal`` method we created in the ``dec-point`` branch.
The ``ContainsDecimal`` method will call the ``EvenOrOddCheck`` method.
We do not need to call the ``EvenOrOddCheck`` method in the ``Main`` method.

Let's copy ``NumberChecks.PositiveOrNegative`` and paste it below ``NumberChecks.ContainsDecimal``.

.. sourcecode:: csharp

   =======
            NumberChecks.ContainsDecimalPoint(input, inputNum);
            NumberChecks.PositiveOrNegative(inputNum);
   >>>>>>> dec-point

We will then ``Accept incoming changes`` or ``Take dec-point``.  
Be sure to test this program to make sure everything is working.  
Once you are happy with the resolved conflict, save and commit your branch.

::

   [main 33975bb] conflicts resolved

This is cause for celebration!  

This was one way to deal with conflict merges.
Use this as a guide as you grow your coding skills.

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
