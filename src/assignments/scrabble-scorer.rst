Assignment #2: Scrabble Scorer
==============================

To see how far your skills have come, we are going to give you a mission to
update our *super* important Scrabble Scorer program. Did you think you were
going to work on Mars rover code already?

The current Scrabble Scorer program takes in a word and returns its point
value. The program needs to be rewritten for two reasons:

#. The dictionary used to store the letter point values is inefficient.
#. The program should have three scoring algorithms and allow the user to pick
   which one to use.

Your updates will make the program more efficient and user friendly.

**Starter Code** can be found here.  Fork the code then clone it to your machine and work on it in Visual Studio.

Requirements
------------

.. admonition:: Note

   The requirements below are what your END assignment will look like.
   This assignment is broken down so you can complete small pieces as you go.
   You need to move sequentially starting at part A below. Please read the
   WHOLE assignment page before starting.

#. Create an ``InitialPrompt`` method that asks the user which scoring
   algorithm to use.
#. Create a ``Transform`` method that takes in the ``oldPointStructure``
   dictionary and *returns* a ``newPointStructure`` dictionary.
#. Code three different scoring functions for assigning points to a word.
#. Create a ``ScoringAlgorithms`` method to invoke one of the three scoring methods. 
#. Create a ``RunProgram`` method to serve as the starting point for your
   program.

Instructions
-------------

.. admonition:: Note

   As you create your methods, think about where the output is best utilized.  Will it be something a user only needs to read?  
   Will it become a parameter for another method?  Revisit the :ref:`Methods introduction chapter <methods>` if you feel unsure.

A) Initial Prompt
^^^^^^^^^^^^^^^^^^

In the starter code, the Scrabble Scorer only uses one scoring algorithm. For
the new version, we want to let the user pick between three algorithms. Define
an ``InitialPrompt`` method that introduces the program and asks the user
which scoring algorithm to use.

Your prompt could look something like:

::

   Welcome to the Scrabble score calculator!

   Which scoring algorithm would you like to use?

   1 - Scrabble: The traditional scoring algorithm.
   2 - Simple Score: Each letter is worth 1 point.
   3 - Bonus Vowels: Vowels are worth 3 pts, and consonants are 1 pt.

   Enter 1, 2 or 3:

B) Transform
^^^^^^^^^^^^^

Currently, the software uses the data structure below for the traditional
Scrabble scoring algorithm. Take a few moments to review how the
``oldPointStructure`` dictionary relates a point value to a letter.
Be sure to notice the data types of this dictionary.

.. sourcecode:: csharp
   :linenos:

   public static Dictionary<int, string> oldPointStructure = new Dictionary<int, string>()
   {
      {1, "A, E, I, O, U, L, N, R, S, T"},
      {2, "D, G"},
      {3, "B, C, M, P" },
      {4, "F, H, V, W, Y" },
      {5, "K" },
      {8, "J, X" },
      {10, "Q, Z" }
   };

The *keys* of ``oldPointStructure`` are the Scrabble points stored as ints, and the
*values* a string of letters. All letters in the array have the Scrabble
point value equal to the key. For example, ``"A"`` and ``"R"`` are worth 1,
``"K"`` is worth 5, and ``"J"`` is worth 8.

To find the point value for a letter with the old format, the program must
iterate over each key in ``oldPointStructure`` and then check if the letter is
inside the array paired with that key. *This search within a search is
inefficient*.

Try it yourself, find ``"L"`` and ``"M"``.  
Unless you have the scrabble scores memorized, you had to search each string.  
Tedious, right?  You can improve this.

Streamlined Score Object
~~~~~~~~~~~~~~~~~~~~~~~~~

It would be better to create a ``newPointStructure`` dictionary that has 26 keys,
one for each letter. The value of each key will be the Scrabble point value.

Examples of the new key storage:

* ``a`` is worth ``1``
* ``b`` is worth ``3``
* ``c`` is worth ``3``
* ``j`` is worth ``8``

In ``newPointStructure``, the letters themselves are keys, so a *single* search
will identify a point value. This is much more efficient than the old method.

.. admonition:: Example

   Example of ``newPointStructure`` dictionary usage.

   .. sourcecode:: csharp

      Console.WriteLine("Scrabble scoring values for");
      Console.WriteLine("letter a: {0}", newPointStructure['a']);
      Console.WriteLine("letter j: {0}", newPointStructure['j']);
      Console.WriteLine("letter z: {0}", newPointStructure['z']);

   **Console Output**

   ::

      Scrabble scoring values for
      letter a:  1
      letter j:  8
      letter z:  10

Do not panic! Instead of tediously hard-coding ``newPointStructure``, use your
clever coding skills to create the new object.


Code the Function   
~~~~~~~~~~~~~~~~~~

#. Write a ``Transform`` method that returns a dictionary and has no parameters. Calling
   ``Transform()`` will *return* a dictionary with *lowercase*
   letters as keys. The value for each key will be the points assigned to that
   letter.
#. Initialize an empty ``newPointStructure`` dictionary by setting it equal to
   ``Transform()``.
#. Points to Consider:

   a. Recall that ``foreach`` loops 
      :ref:`iterate over the key/value pairs <kvp-foreach>` within an dictionary.
   b. If you need a reminder of how to assign new key/value pairs, review the
      :ref:`relevant section <initialize-dictionary>` in the
      ``Control Flow and Collections`` chapter.
   c. To access the string of letters within ``oldPointStructure``, use bracket
      notation (``oldPointStructure[key]``).
   d. To access a particular element within a string, 
      consider what :ref:`strings are made of <string-chars>` and 
      the various :ref:`string methods <string-method-examples>` you can use to access them.

      .. admonition:: Examples

         .. sourcecode:: CSharp
            :linenos:

            Console.WriteLine("Letters with score 4: {0}", oldPointStructure[4]);
            
            foreach(char ch in oldPointStructure[4])
            {
                Console.Write(ch + "-");  //dash used to visually separate each char 
            }

         **Console Output**

         ::

            Letters with score 4: F, H, V, W, Y

            F-,- -H-,- -V-,- -W-,- -Y-


C) Scoring Algorithms
^^^^^^^^^^^^^^^^^^^^^^

Create a *separate* method for each of the following scoring algorithms.

#. **Simple Score:** Define a method that takes a word as a parameter and
   displays a score. Each letter within the word is worth 1 point.
#. **Bonus Vowels:** Define a method that takes a word as a parameter and
   displays a score. Each vowel within the word is worth 3 points, and each
   consonant is worth 1 point.
#. **Scrabble Score:** Define a method that takes a word as a parameter and displays a score. 
   The method uses the *transformed* ``newPointStructure``.
#. Each method should have a way to display the *original* word and the total value of points.
   (*Consider:* how many word parameters will you be working with?)

.. admonition:: Examples

   .. sourcecode:: csharp

      ScrabbleScorer("taxi");
      //Output: Your word: taxi is worth 11

      SimpleScorer("taxi");
      //Output: Your word: taxi is worth 4

      BonusVowels("taxi");
      //Output: Your word: taxi is worth 8




Define ScoringAlgorithms method
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Create an method that will pass the user's word to the selected scoring method.
   This method will need parameters for which score method they select and the user's word.
#. Use the selected algorithm to determine the score for the word:

   a. If the user enters ``1`` or an invalid option, use the Scrabble Scorer method.
   b. If the user entered ``2``, use the Simple Score method.
   c. If the user entered ``3``, use the Bonus Vowels method.

#. Things to Ponder:

   a. Think about what each parameter will be doing and how it could be used.
   b. Think about how to reach the desired scoring method.


Take a Breath
~~~~~~~~~~~~~~

Good! Your ``ScoringAlgorithms`` method now invokes all of the scoring
options and passes the word to score to each.  Looks like we have a good start on this Scrabble program.

To access a scoring method via ``ScoringAlgorithms``,  call it and pass the score option and a test word.

.. admonition:: Examples

   .. sourcecode:: csharp

      // Scrabble scoring
      ScoringAlgorithms(1, "taxi");
         //Output: Your score for "taxi": 11

      // Simple scoring
      ScoringAlgorithms(2, "taxi");
         //Output: Your score for "taxi": 4

      // Bonus Vowel scoring
      ScoringAlgorithms(3, "taxi");
         //Output: Your score for "taxi": 8


D) Tie it All Together
^^^^^^^^^^^^^^^^^^^^^^^

Define a ``RunProgram`` method that will do the following when called:

#. Invoke ``InitialPrompt`` to pick the algorithm.
#. Prompt the user to enter a word to score. The prompt should also provide the
   user an option for ending the program.
#. When taking in a user's word, should account for case.
#. Invoke the ``ScoringAlgorithms`` method with the correct parameters.
#. Display the score for the word.
#. Repeat steps 2 to 4 until the user ends the program by entering ``"Stop"``.
   (*Consider*: Should this check be case-insensitive?)

Test Words
-----------

Here are some words you can use to test your code:

#. ``CSharp`` = 13 points using Scrabble, 6 using Simple Score, and 8
   using Bonus Vowels.
#. ``Scrabble`` = 14 points using Scrabble, 8 using Simple Score, and 12 using
   Bonus Vowels.
#. ``Zox`` = 19 points using Scrabble, 3 using Simple Score, and 5 using Bonus
   Vowels.

.. _example-output:

Example Output
^^^^^^^^^^^^^^

::

   Welcome to the Scrabble score calculator!

   Which scoring algorithm would you like to use?

   1 - Scrabble: The traditional scoring algorithm.
   2 - Simple Score: Each letter is worth 1 point.
   3 - Bonus Vowels: Vowels are worth 3 pts, and consonants are 1 pt.

   Enter 1, 2, or 3:

   Enter a word to be scored, or "Stop" to quit:  LaunchCode
   Your score for "LaunchCode": 18

   Enter a word to be scored, or "Stop" to quit:  Rocket
   Your score for "Rocket": 12

   Enter a word to be scored, or "Stop" to quit: stop

Bonus Missions
---------------

#. Currently, the prompts accept ANY input values. The user could enter
   something *other* than 1, 2, or 3 when selecting the scoring algorithm, and
   they could enter numbers or symbols when asked for a word. Modify your code
   to reject invalid inputs and then re-prompt the user for the correct
   information.
#. Score words spelled with blank tiles by adding ``' '`` to the
   ``newPointStructure`` object. The point value for a blank tile is ``0``.

Submitting Your Work
---------------------

#. Finish the assignment.
#. ``commit`` and ``push`` your work to a repository on your GitHub profile.
#. Find the corresponding Canvas assignment on 
   `learn.launchcode.org <https://learn.launchcode.org/>`_ and enter the GitHub URL for your project.
#. Find a TA and demo your project for them.

