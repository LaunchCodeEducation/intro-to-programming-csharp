Exercises: Strings
==================

Part One
--------

#. Identify the result for each of the following statements.  Don't forget your data types!

   #. ``"C Sharp"[5]``
   #. ``"Strings are sequences of characters."[5]``
   #. ``"Wonderful".Length``
   #. ``"Do spaces count?".Length``

   *There's no code snippet for this one, just try it on your own with old-fashioned 
   pen and paper!*

#. The ``Length`` method returns how many characters are in a string. However,
   the method will NOT give us the length of a number. If ``int num = 1001``,
   ``num.Length`` will throw an error and remind you about data types.

   #. Use type conversion to print the length (number of digits) of an integer.
   #. Print the number of digits in a DOUBLE value (e.g. ``double num = 123.45`` has 5
      digits but a length of 6).
      
      #. Modify your code to print out the length of a double value EXCLUDING the period.

   #. What if ``num`` could be EITHER an integer or a double?  Add an ``if/else``
      statement so your code can handle both cases.  (Hint: Consider the
      ``IndexOf()`` or ``Contains()`` string methods).

   `Code it at repl.it <https://repl.it/@launchcode/StringExercises02-CSharp/>`__

Part Two
--------

1. Remember, strings are *immutable*. Consider a string that represents a
   strand of DNA: ``string dna = " TCG-TAC-gaC-TAC-CGT-CAG-ACT-TAa-CcA-GTC-cAt-AGA-GCT    "``.
   There are some typos in the string that we would like to fix:

   #. Use the ``Trim()`` method to remove the leading and trailing whitespace,
      and then print the results.
   #. Change all of the letters in the dna string to UPPERCASE and print the
      result.
   #. Note that if you try ``Console.WriteLine(dna)`` after applying the methods, the
      original, flawed string is displayed. To fix this, you need to
      *reassign* the changes back to ``dna``. Apply these fixes to your
      code so that ``Console.WriteLine(dna)`` prints the DNA strand in UPPERCASE
      with no whitespace.

   `Code it at repl.it <https://repl.it/@launchcode/StringExercises03-CSharp/>`__

2. Let's use string methods to do more work on the DNA strand:

   #. Replace the sequence ``"GCT"`` with ``'AGG'``, and then print the altered
      strand.
   #. Look for the sequence ``"CAT"`` with ``IndexOf()``. If found print, ``"CAT
      found"``, otherwise print, ``"CAT NOT found"``.
   #. Use ``Substring()`` to print out the fifth set of 3 characters (called a **codon**)
      from the DNA strand.
   #. Use string interpolation to print, ``"The DNA strand is ___ characters long."``
   #. Just for fun, apply methods to ``dna`` and use another string interpolation to
      print, ``"taco cat"``.

   `Code it at repl.it <https://repl.it/@launchcode/DNA-Strings-CSharp/>`__

Part Three
----------

1. If we want to turn the string ``"C Sharp"`` into ``"CS"``, we might try
   ``.Remove()``.  Too easy.  Let's use our cleverness to achieve the same result and practice with other C# methods.

   #. Use string concatenation and two ``Substring()`` methods to print ``"CS"`` from
      ``"C Sharp"``.
   #. Without using ``Substring()``, use method chaining to accomplish the same
      thing.
   #. Use bracket notation and string interpolation to print, ``"The abbreviation for
      "C Sharp" is "CS."`` Don't forget about your escape characters.
   #. Just for fun, try chaining 3 or more methods together, and then print the
      result.

   `Code it at repl.it <https://repl.it/@launchcode/StringExercises05-CSharp/>`__

2. Some programming languages (like Python) include a ``title()`` method to
   return a string with Every Word Capitalized (e.g. ``'title case'.title()``
   returns ``Title Case``).  C# has no ``title()`` method, but that
   won't stop us! Use the string methods you know to print ``"Title Case"``
   from the string ``"title case"``.

   `Code it at repl.it <https://repl.it/@launchcode/StringExercises06-CSharp/>`__
