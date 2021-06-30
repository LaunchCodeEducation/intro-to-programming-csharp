=================
Bracket Notation
=================

Understanding strings as sequential collections of characters gives us much more than just a mental model of how they are structured. 
C# provides a rich collection of tools---including special syntax and operations---that allows us to work with strings.

.. index:: ! bracket notation, ! index

.. index:: 
   single: string; index

**Bracket notation** is the special syntax that allows us to access the individual characters that make up a string. 
To access a character, we use the syntax ``someString[i]``, where ``i`` is the **index** of the character we want to access. 
String indices are integers representing the position of a character within a given string, and they start at 0. 
Thus, the first character of a string has index 0, the second has index 1, and so on.

Consider the string ``"C Sharp"``. The ``'C'`` has index 0, the whitespace ``' '`` has index 1, ``'S'`` has index 2, and so on.  
When referring to these indices, we switch to the **char** data type.

.. figure:: figures/string-indices-csharp.png
   :alt: The string "C Sharp" with indices labeled below each letter

   The indices of a string.

An expression of the form ``someString[i]`` gives the character at index ``i``.

.. admonition:: Example

   This program prints out the initials of the person's name.

   .. sourcecode:: csharp
      :linenos:
   
      string csDesigner = "Anders Hejlsberg";
      char firstInitial = csDesigner[0];
      char lastInitial = csDesigner[7];

      string outputStr = "C Sharp was designed by somebody with initials " + 
         firstInitial + "." +
         lastInitial + ".";

      Console.WriteLine(outputStr);

   **Console Output**

   ::

      C Sharp was designed by somebody with initials A.H.

What happens if we try to access an index that doesn't exist, for example -1 or an index larger than the length of the string?

.. admonition:: Try It!

   .. replit:: csharp
      :linenos:
      :slug: Invalid-String-Indices-CSharp
   
      string csDesigner = "Anders Hejlsberg";

      Console.WriteLine(csDesigner[-1]);
      Console.WriteLine(csDesigner[42]);

.. admonition:: Question

   What does an expression using bracket notation evaluate to when the index is invalid (the index does not correspond to a character in the string)?

Check Your Understanding
------------------------

.. admonition:: Question

   If ``string phrase = "Code for fun"``, then ``phrase[2]`` evaluates to:

   #. ``'o'``
   #. ``'d'``
   #. ``"for"``
   #. ``"fun"``

.. ans: b. ``'d'``

.. admonition:: Question

   Which of the following returns ``true`` given ``string myStr = "Index"``?  Choose all correct answers.

   #. ``myStr[2] == 'n';``
   #. ``myStr[4] == 'x';``
   #. ``myStr[1] == 'e';``
   #. ``myStr[0] == 'I';``

.. admonition:: Question

   What is printed by the following code?

   .. sourcecode:: csharp
      :linenos:

      string phrase = "C Sharp rocks!";
      Console.WriteLine(phrase[phrase.length - 8]);

   #. ``'p'``
   #. ``' '``
   #. ``'o'``
   #. ``'s'``
