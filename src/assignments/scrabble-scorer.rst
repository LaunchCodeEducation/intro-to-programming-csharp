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
*values* a string letters. All letters in the array have the Scrabble
point value equal to the key. For example, ``"A"`` and ``"R"`` are worth 1,
``"K"`` is worth 5, and ``"J"`` is worth 8.

To find the point value for a letter with the old format, the program must
iterate over each key in ``oldPointStructure`` and then check if the letter is
inside the array paired with that key. *This search within a search is
inefficient*.

Try it yourself, find ``"L"`` and ``"M"``.  Unless you have the scrabble scores memorized, you had to search each string.  Tedious, right?
You can improve this.

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

Code the Function   **<----  Pick up here**
~~~~~~~~~~~~~~~~~~

#. Write a ``Transform`` method that returns a dictionary and has no parameters. Calling
   ``Transform()`` will return a dictionary with *lowercase*
   letters as keys. The value for each key will be the points assigned to that
   letter.
#. Initialize an empty ``newPointStructure`` dictionary by setting it equal to
   ``Transform()``.
#. Hints:

   a. Recall that ``foreach`` loops iterate over the keys within an dictionary.
   b. If you need a reminder of how to assign new key/value pairs, review the
      :ref:`relevant section <add-new-object-properties>` in the
      ``Objects and Math`` chapter.
   c. To access the letter arrays within ``oldPointStructure``, use bracket
      notation (``oldPointStructure['key']``).
   d. To access a particular element within a letter array, add a second set of
      brackets (``oldPointStructure['key'][index]``), or assign the array to a
      variable and use ``variableName[index]``.

      .. admonition:: Examples

         .. sourcecode:: JavaScript
            :linenos:

            console.log("Letters with score '4':", oldPointStructure['4']);
            console.log("3rd letter within the key '4' array:", oldPointStructure['4'][2]);

            let letters = oldPointStructure['8'];
            console.log("Letters with score '8':", letters);
            console.log("2nd letter within the key '8' array:", letters[1]);

         **Console Output**

         ::

            Letters with score '4': [ 'F', 'H', 'V', 'W', 'Y' ]
            3rd letter within the key '4' array: V

            Letters with score '8': [ 'J', 'X' ]
            2nd letter within the key '8' array: X

C) Scoring Algorithms
^^^^^^^^^^^^^^^^^^^^^^

Create a separate function for each of the following scoring algorithms.

.. admonition:: Note

   Make each scoring algorithm case *insensitive*, meaning that they
   should all ignore case when assigning points.

#. **Simple Score:** Define a function that takes a word as a parameter and
   returns a score. Each letter within the word is worth 1 point.
#. **Bonus Vowels:** Define a function that takes a word as a parameter and
   returns a score. Each vowel within the word is worth 3 points, and each
   consonant is worth 1 point.
#. **Scrabble Score:** Define a function that takes a word and
   ``newPointStructure`` as parameters and returns a score. The function uses
   the data stored in ``newPointStructure`` to determine the point value for
   the word.

Define Scoring Objects
~~~~~~~~~~~~~~~~~~~~~~~

#. Create an object for each of the three scoring options. Each object should
   contain three keys: ``name``, ``description``, and ``scoreFunction``.
#. Examine the table for the information to store in ``name`` and
   ``description``. The ``scoreFunction`` for each object should be the name of
   one of the algorithms you defined above.

   .. list-table::
      :header-rows: 1

      * - Name
        - Description
        - Score Function
      * - Scrabble
        - The traditional scoring algorithm.
        - Uses the ``newPointStructure`` object to determine the score for a given
          ``word``.
      * - Simple Score
        - Each letter is worth 1 point.
        - A function with a ``word`` parameter that returns a score.
      * - Bonus Vowels
        - Vowels are 3 pts, consonants are 1 pt.
        - A function with a ``word`` parameter that returns a score based on the
          number of vowels and consonants.

#. Create a ``scoringAlgorithms`` array to hold your three scorer objects.

Take a Breath
~~~~~~~~~~~~~~

Good! Your ``scoringAlgorithms`` structure now holds all of the scoring
information required for the new Scrabble program.

To access a scoring object and its properties, use a combination of bracket
notation and dot notation.

.. admonition:: Examples

   .. sourcecode:: js

      // Scrabble scoring
      console.log("algorithm name: ", scoringAlgorithms[0].name);
      console.log("scoreFunction result: ", scoringAlgorithms[0].scoreFunction("JavaScript", newPointStructure));
      // Simple scoring
      console.log("algorithm name: ", scoringAlgorithms[1].name);
      console.log("scoreFunction result: ", scoringAlgorithms[1].scoreFunction("JavaScript"));
      // Bonus Vowel scoring
      console.log("algorithm name: ", scoringAlgorithms[2].name);
      console.log("scoreFunction result: ", scoringAlgorithms[2].scoreFunction("JavaScript"));

   Console Output

   ::

      algorithm name:  Scrabble
      scoreFunction result:  24
      algorithm name:  Simple Score
      scoreFunction result:  10
      algorithm name:  Bonus Vowels
      scoreFunction result:  16

D) Tie it All Together
^^^^^^^^^^^^^^^^^^^^^^^

Define a ``runProgram`` function that will:

#. Accept the ``scoringAlgorithms`` array as an argument.
#. Use ``initialPrompt`` to pick the algorithm.
#. Prompt the user to enter a word to score. The prompt should also provide the
   user an option for ending the program.
#. Use the selected algorithm to determine the score for the word:

   a. If the user enters ``0`` or an invalid option, use the Scrabble
      ``scoreFunction``.
   b. If the user entered ``1``, use the Simple Score ``scoreFunction``.
   c. If the user entered ``2``, use the Bonus Vowels ``scoreFunction``.

#. Display the score for the word.
#. Repeat steps 3 to 5 until the user ends the program by entering ``'Stop'``.
   (*Consider*: Should this check be case-insensitive?)

Test Words
-----------

Here are some words you can use to test your code:

#. ``JavaScript`` = 24 points using Scrabble, 10 using Simple Score, and 16
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

   0 - Scrabble: The traditional scoring algorithm.
   1 - Simple Score: Each letter is worth 1 point.
   2 - Bonus Vowels: Vowels are worth 3 pts, and consonants are 1 pt.

   Enter 0, 1, or 2: 0

   Using algorithm: Scrabble

   Enter a word to be scored, or 'Stop' to quit:  LaunchCode
   Score for 'LaunchCode': 18

   Enter a word to be scored, or 'Stop' to quit:  Rocket
   Score for 'Rocket': 12

   Enter a word to be scored, or 'Stop' to quit: stop

Bonus Missions
---------------

#. Currently, the prompts accept ANY input values. The user could enter
   something *other* than 0, 1, or 2 when selecting the scoring algorithm, and
   they could enter numbers or symbols when asked for a word. Modify your code
   to reject invalid inputs and then re-prompt the user for the correct
   information.
#. Score words spelled with blank tiles by adding ``' '`` to the
   ``newPointStructure`` object. The point value for a blank tile is ``0``.

Submitting Your Work
---------------------

#. From the address bar at the top of the browser window, copy the URL of the
   repl.it that contains your solution.
#. Go to the Graded Assignment #2 page in Canvas and click *Submit Assignment*.
#. Paste the URL into the Website URL input.
#. Click *Submit Assignment* again.
#. Notify your TA that your assignment is ready to be graded.
