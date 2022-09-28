Bonus Mission: Merge Conflicts!
-------------------------------

Merge Conflicts!
^^^^^^^^^^^^^^^^

When collaborating on a project, things won’t always go smoothly. 
It’s common for two people to make changes to the same line(s) of code, 
at the same time, preventing Git from being able to merge the changes together.

.. figure:: figures/studio/git-merge.gif
   :alt: An animated GIF file showing two opposing armies colliding in a mess

   Git Merge Conflicts

This isn't such a big deal. In fact, it's very common. To see how we can handle
such a situation, we'll intentionally create a merge conflict and then resolve
it.

**Pilot**: 
   #. Checkout the ``main`` branch.
   #. Change the Console.BackgroundColor again and save your work.
   #. ``commit`` and ``push`` up your changes to ``main``.

Meanwhile...

**Control**: 
   #. Checkout a new branch called ``color-update``.
   #. Change the Background color.
   #. ``commit`` and ``push`` up your changes.
   #. Create a pull request.   You will receive a message that you are not able to merge this branch into ``main``, and that is okay.
      There are merge conflicts, but Pilot will be handling them at this point.

Resolving Merge Conflicts
^^^^^^^^^^^^^^^^^^^^^^^^^

**Pilot**: 
   #. ``pull`` down the latest ``main`` to check for updates.
   #. Look for Control's ``color-update`` branch.  
   #. If you don't see it, run the following command: ``git branch -a``.
   #. Merge the ``color-update`` branch into ``main`` using the following command:

      .. sourcecode:: bash

         $ git merge origin/color-update
   
   #. Note the output.

      .. sourcecode:: bash

            $ git merge origin/color-update
            Auto-merging communication-log/Program.cs
            CONFLICT (Content): Merge conflict in communication-log/Program.cs
            Automatic merge failed: fix conflicts and commit the result.

      That is great feedback!  Git has detected conflicting code and has noted its location for you.

   #. Open your IDE and look in the file git pointed out.  Look for the conflict symbols.

      .. admonition:: Note

         Merge conflicts may appear different based on your IDE and if you are using a Mac or Windows computer.
         The symbols are the same.  Look for the following :ref:`symbols<merge-conflict>` in your code: ``<<<<<<<``,  ``=======`` and ``>>>>>>>``.

   #. Once you find the conflict, it is up to you to decide which code to keep.
   #. Save your changes, ``commit``, and ``push`` up to ``main``.


      .. admonition:: Note
         
         Many code editors have buttons to resolve merge conflicts with a single click. 
         There’s nothing magic about these buttons; they do the same thing that you can do by editing the file.
         
         Feel free to use them, but beware that they will not always work. 
         If you need to incorporate parts of a change from **both** branches, 
         resolve the conflict by manually editing.
  

Pulling the Merged Code
^^^^^^^^^^^^^^^^^^^^^^^

**Control**: 
   #. While Pilot is working on a merge conflict, checkout your ``main`` branch and run a git status.

      .. sourcecode:: bash

         $ git status
         On branch main
         Your branch is up-to-date with 'origin/main'.
         nothing to commit, working directory clean

      Your local Git thinks the status is quo. Little does it know that up at GitHub, the status is *not* quo.  
      Depending on where Pilot is when you run this status, the git message will be a little different. 
      If git detects changes between branches, it will tell you and offer suggestions to ``pull``.

   #. We'd find this out by doing either a ``git fetch``, or if we just want the latest version of this branch, ``git pull``:

      .. sourcecode:: bash

         $ git pull
         remote: Counting objects: 13, done.
         remote: Compressing objects: 100% (8/8), done.
         remote: Total 13 (delta 4), reused 13 (delta 4), pack-reused 0
         Unpacking objects: 100% (13/13), done.
         From Github.com:chrisbay/communication-log
            0c21659..e0de62d  main     -> origin/main
         Updating 0c21659..e0de62d
         Fast-forward
         communication-log.sln | 3 ++-
         1 file changed, 4 insertions(+), 3 deletions(-)

Great Scott! Looks like Pilot changed the ``communication-log``.
Note that Control didn't have to deal with the hassle of resolving merge
conflicts. Since Control intervened, Git assumes that the team is okay with the
way they resolved it, and *fast forwards* our local repo to be in sync with the
remote one. Let's look at ``communication-log.sln`` to make sure.  
What do you see?  What color is the text now?  Oh my!


More Merge Conflicts! (Bonus of the Bonus)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Let's turn the tables on the steps we just carried out, so Pilot can practice
resolving merge conflicts.

#. **Control and Pilot**: Confer to determine the particular lines in the code
   that you will both change. Make different changes in those places.
#. **Control**: Stage, ``commit``, and ``push`` your changes.
#. **Control**: Try to ``pull`` in Pilot's changes, and notice that there are merge
   conflicts. Resolve these conflicts as we did above (ask Pilot for help, if
   you're uncertain about the process). Then stage, ``commit``, and ``push`` your
   changes.
#. **Pilot**: ``pull`` in the changes that Control pushed, including the resolved 
   merge conflicts.

Merge conflicts are a part of the process of team development. Resolve them to avoid bugs in your code.

Avoiding Conflicts
^^^^^^^^^^^^^^^^^^

Git happens. Merge conflicts will pop up, but they're not a big deal. 
Still, the best way to handle them is to try to avoid them in the first place. Here are some tips:

#. Deal with any uncommitted work before trying to merge.
#. Partners should avoid working on the same file at the same time.
#. Try to avoid adding code directly into ``main``. Explore new ideas in a different branch first and then merged.



