Studio: Communication Log
==========================

Getting Ready: Code Together
----------------------------

Coding together allows you to work as a team so you can build bigger projects faster.

In this studio, we will practice the common Git commands used when multiple people work on the same code base.

You and a partner will begin by coding in tag-team shifts. By the end of the task you should have a good idea about how to have two people work on the same code at the same time. You will learn how to:

Quickly add code in pull + push cycles (Important! This is the fundamental process!)
Add a collaborator to a GitHub Project
Share repositories on GitHub
Create a branch in Git
Create a pull request in GitHub
Resolve merge conflicts (which are not as scary as they sound)
This lesson reinforces:

Creating repositories
Cloning repositories
Working with Git concepts: Staging, Commits, and Status

Overview
--------

The instructor will discuss why GitHub is worth learning. You already know how to use a local Git repository with one branch, giving you the ability to move your code forward and backward in time. Working with branches on GitHub extends this ability by allowing multiple people to build different features at the same time, then combine their work. Pull requests act as checkpoints when code flows from branch to branch.

Students must pair off for this exercise. If you have trouble finding a partner, ask your TA for help.


We are going to simulate a radio conversation between the shuttle pilot and
mission control.

First, find a new friend to share the activity.

You and your partner will alternate tasks, so designate one of you as **Pilot**
and the other as **Control**. Even when it is not your turn to complete a task,
read and observe what your partner is doing to complete theirs. The steps here
mimic how a real-world collaborative Git workflow can be used within a project.

.. _create-new-git-repo:

Step 1: Create a New Repository
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. admonition:: Note

   Be careful if you try to use ``copy/paste`` with the ``git`` commands! The
   ``$`` symbols in the screenshots represent to the prompts in the terminal.
   They are NOT part of the commands.

Windows instructions:
---------------------

**Control**: Navigate to your development folder and enter the following 3 commands to create a new project.
   
   ::

      $ mkdir communication-log
      $ cd communication-log
      $ git init

Now that you have a directory, open Visual Studio and :ref:`create a new console project <create-new-csharp-project>`.  

   .. figure:: figures/studio/name-location-verControl.png
      :alt: Name your solution and select location for your files.
      
      Give your solution and project a name (1).  Typically they will have the same name.  Then select the directory to store your files (2).  Browse for the directory you just created.  
      
   .. admonition:: Setting Up a ``.gitignore`` File

      A ``.gitignore`` file, is a text file will contain untracked files, or ignored filed.
      These are files that will become part of your repo, but are not very useful to other developers.
      Placing them in a ``.gitignore`` file will tell git to skip over them, which will reduce visual clutter in your terminal.
   
      **Windows Users**: There are a few steps to create a ``.gitignore file``.

      #. Select the **Git** tab.  Scroll down to **Settings**.

         .. figure:: figures/studio/git-settings-tab.png
            :scale: 60%
            :alt: Select the Settings for Git in Visual Studio

      #. **Settings** will open the **Source Control** option.
         Under **Sorce Control** select **Git Repository Settings** then **General**
         in the right-side pane, look for the *Git files* section.
         Select **Add** for **Ignore file:**
         Select **OK** to add your new files.

         .. figure:: figures/studio/win-ignore-files.png
            :scale: 60%
            :alt: View of the General Git Repository Settins.


      Again, this is only one way to create this type of file.  
      Use it as a starting point, and grow from here.


Mac Instructions:
-----------------

**Control**: Open Visual Studio and :ref:`create a new project <create-new-csharp-project>`.  

.. figure:: figures/studio/nameAndLocation.png
   :width: 75%
   :alt: Name your solution and select location for your files.

   Give your solution and project a name (1).  Typically they will have the same name.  Then 
   select the directory to store your files (2). Check the boxes to use git for version control 
   and automatically create a ``.gitignore file`` (3).

Step 2: First Commit
^^^^^^^^^^^^^^^^^^^^

Let's check that our project works by running it.

.. admonition:: Note

   If your console window does not stay open long enough for you to see your code, try adding the ``Console.Read()`` below the ``WriteLine``.
   This is a piece of code that will keep your terminal window open so you can read what it contains.
   
   If you can read your terminal window just fine and you haven't added anything, then ignore this tip.

Open the terminal that is part of Visual Studio. It can be found under the **View** tab.

Once you've checked this file in the terminal, let's stage and commit it.

#. First, check the ``status``.

   ::

      $ git status
      On branch main

      No commits yet.

      Untracked files:
      (use "Git add <file>..." to include in what will be committed)

         communication-log.sln
         communication-log/Program.cs
         communication-log/communication-log.csproj

      nothing added to commit but untracked files present (use "git add" to track)

#. The output shows us that we have three new files that have not been staged yet. Let's ``add``
   everything in this directory, then check the ``status`` again.

   ::

      $ git add .
      $ git status
      On branch main

      No commits yet

      Changes to be committed:
      (use "git rm --cached <file>..." to unstage)

         new file:  communication-log.sln
         new file:  communication-log/Program.cs
         new file:  communication-log/communication-log.csproj

#. The output tells us that the files are staged. Now let's ``commit``. After
   that, we can see a record of our progress by using ``git log``.

   ::

      $ git commit -m 'Started communication log.'
      [main (root-commit) e1c1719] Started communication log.
      4 files changed, 451 insertions(+)
      create mode 100644 .gitignore
      create mode 100644 communication-log.sln
      create mode 100644 communication-log/Program.cs
      create mode 100644 communication-log/communication-log.csproj

      $ git log
      commit 679de772612099c77891d2a3fab12af8db08b651
      Author: Cheryl <chrisbay@gmail.com>
      Date:   Wed Apr 5 10:55:56 2017 -0500

         Started communication log.

Great! We've got our project going locally, but we're going to need to make it
accessible for **Pilot** also. Let's push this project up to GitHub.

Step 3: Share Your Repository On GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Control**: Go to your GitHub profile in a web browser. Click on the "+"
button to add a new repository (called a *repo* for short).

.. figure:: figures/studio/new-repo-button.png
   :alt: The New Repository link in the dropdown menu at top right on GitHub.

   The *New Repository* link is in the dropdown menu at top right on GitHub.

To create a new repository:

#. Fill in the name and description. 
#. Uncheck *Initialize this repository with a README* and click *Create Repository*.

.. figure:: figures/studio/create-repo.png
   :alt: Creating a new repository in GitHub by filling out the form

   Create a new repository in GitHub

.. admonition:: Note

   If you initialize with a README, in the next step Git will refuse to merge
   this repo with the local repo. There are ways around that, but it's faster
   and easier to just create an empty repo here.

After clicking, you should see something similar to:

.. figure:: figures/studio/new-repo-push-main.png
   :alt: The page you see after creating an empty repository, with several options.

   Connecting to a repository in GitHub

Now go back to your terminal and copy/paste the commands shown in the GitHub
instructions. These should be very similar to:

::

   $ git remote add origin https://github.com/your-username/communication-log.git
   $ git branch -M main
   $ git push -u origin main

.. admonition:: Note

   The first time you push up to GitHub, you will be prompted in the terminal
   to enter your account username and password. Do this.
   
   You will then see a large amount of output that you can safely ignore. The
   final few lines will confirm a successful push. They will look something
   like this:

   ::

      To github.com:your-username/communication-log.git
         c7f97814..54993de3  main -> main

   Notice that if your local branch was named ``master`` it was automatically changed to ``main``.

.. admonition:: Warning

   Unless you've set up an SSH key with GitHub, make sure you've selected the
   HTTPS clone URL. If you're not sure whether you have an SSH key, you
   probably don't.

Now you should be able to confirm that GitHub has the same version as your
local project. (File contents in browser match those in terminal). Click around
and see what is there. You can read all your code through GitHub's web
interface.

.. figure:: figures/studio/repo-first-commit.png
   :alt: A repository with one commit in GitHub

   A repository with one commit in GitHub

.. _clone-from-git:

Step 4: Clone a Project from GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Pilot**: Go to Control's GitHub profile and find the communication-log repo.
Click on the green *Clone or download* button. Use HTTPS (not SSH). Copy the
url to your clipboard.

.. figure:: figures/studio/clone-button.png
   :alt: The clone button is on the right-hand side of a project's main page

   Cloning a repository in GitHub

In your terminal, navigate to your development folder and clone down the repo.
The command should look something like this.

::

   $ git clone https://github.com/chrisbay/communication-log.git

Now you can respond to Control! Open the ``communication-log.sln`` file in your editor and
add your response to mission control. Be creative, the communication can go
anywhere! Just don't ask your partner what you should write. After you finish,
commit your change.

.. admonition:: Note

   When you open the project folder, you might not be in the same directory as the solution.  
   You want to open the solution or ``.sln`` file.  
   A quick way to do that from the terminal is to ``cd`` into the folder that is holding the solution and then type ``open .sln``.

::

   $ git status
   On branch main
   Your branch is up-to-date with 'origin/main'.
   nothing to commit, working directory clean
   $ git add .
   $ git commit -m 'Added second line to log.'

Now we need to push up your changes so Control can use them as well.

::

   $ git push origin main
   ERROR: Permission to chrisbay/communication-log.git denied to pilot.
   fatal: Could not read from remote repository.

   Please make sure you have the correct access rights
   and the repository exists.

Great error message! It let us know exactly what went wrong: Pilot does not
have security permissions to write to Control's repo. Let's fix that.

Step 5: Add A Collaborator To A GitHub Project
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Control**: In your web browser, go to your ``communication-log`` repo. Click
the *Settings* button then click on *Collaborators*. Enter in Pilot's GitHub
username and click *Add Collaborator*.

.. figure:: figures/studio/add-collaborator.png
   :alt: Add a collaborator by typing their user name into the input on the Add Collaborator page.

   Add a collaborator to your repo in GitHub

Step 6: Join the Project and Push
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Pilot**: You should receive an email invitation to join this repository.
View and accept the invitation.

.. note::

   If you don't see an email (it may take a few minutes to arrive in your inbox),
   check your Spam folder. If you still don't have an email, visit the
   repository page for the repo that Control created (ask them for the link), and
   you'll see a notification at the top of the page.

.. figure:: figures/studio/repo-invite.png
   :alt: The email invite to join a GitHub repository
   :height: 400px

   Invited to collaborate email in GitHub

Now let's go enter that command again to push up our code.

::

   $ git push origin main
   Counting objects: 9, done.
   Delta compression using up to 4 threads.
   Compressing objects: 100% (9/9), done.
   Writing objects: 100% (9/9), 1.01 KiB | 0 bytes/s, done.
   Total 9 (delta 8), reused 0 (delta 0)
   remote: Resolving deltas: 100% (8/8), completed with 8 local objects.
   To git@github.com:chrisbay/communication-log.git
      511239a..679de77  main -> main

Anyone reading the code through GitHub's browser interface should now see the
new second line.



