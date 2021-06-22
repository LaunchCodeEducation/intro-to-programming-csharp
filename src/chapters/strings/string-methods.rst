.. _string-methods:

===============
String Methods
===============

C# provides many useful methods for string objects. 
Recall that a method is a function that "belongs to" a specific object. 
Methods will typically result in some operation being carried out on the data within an object. 
For strings, this means that our methods will typically transform the characters of the given string in some way.
This transformation will either be a modified copy of the original string, or a new instance of the string.  

As we have learned, strings are immutable. Therefore, string methods will not change the value of a string itself, 
but instead will *return* a new string that is the result of the given operation.  

We saw this behavior in the ``ToLower`` example.

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      string nonprofit = "LaunchCode";

      Console.WriteLine(nonprofit.ToLower());
      Console.WriteLine(nonprofit);

   **Console Output**

   ::

      launchcode
      LaunchCode

While ``nonprofit.ToLower()`` evaluated to ``"launchcode"``, the value of ``nonprofit`` was left unchanged. This will be case for each of the string methods.

Common String Methods
---------------------

.. index::
   single: string; methods

Here we present the most commonly-used string methods. You can find documentation for other string methods at:

- `W3Schools <https://www.w3schools.com/cs/cs_strings.asp>`_
- `Microsoft Documentation <https://docs.microsoft.com/en-us/dotnet/api/system.string?view=net-5.0>`_


.. list-table:: Common String Methods
   :header-rows: 1

   * - Method
     - Syntax
     - Description
   * - :ref:`IndexOf <string-indexof-examples>`
     - ``stringName.IndexOf(substr)``
     - Returns the index of the first occurrence of the substring in the string, and returns -1 if the substring is not found.
   * - :ref:`Contains <string-contains-examples>`
     - ``stringName.Contains(substr)``
     - Returns a boolean value if a specified string value is present.
   * - :ref:`ToLower <string-tolower-examples>`
     - ``stringName.ToLower()``
     - Returns a copy of the given string, with all uppercase letters converted to lowercase.
   * - :ref:`ToUpper <string-toupper-examples>`
     - ``stringName.ToUpper()``
     - Returns a copy of the given string, with all lowercase letters converted to uppercase.
   * - :ref:`Trim <string-trim-examples>`
     - ``stringName.Trim()``
     - Returns a copy of the given string with the leading and trailing whitespace removed.
   * - :ref:`Replace <string-replace-examples>`
     - ``stringName.Replace(searchChar, replacementChar)``
     - Returns a copy of ``stringName`` with the **all** occurrence of ``searchChar`` replaced by ``replacementChar``.
   * - :ref:`Substring <string-substring-examples>`
     - ``stringName.Substring(i, j)``
     - Returns the substring consisting of characters from index ``i`` for a length of ``j``.
   * - :ref:`Split <split-string-examples>`
     - ``stringName.Split(delimiter)``
     - Splits the string into sections at each ``delimiter`` and stores the sections as elements in an array.
   * - :ref:`Insert <string-insert-examples>`
     - ``stringName.Insert(i, substring)``
     - Returns new ``stringName`` in which a specific substring has been inserted at index ``i``.
   * - :ref:`Remove <string-remove-examples>`
     - ``stringName.Remove(i, j)``
     - Returns new string after certain number of characters have been deleted from current string.
   * - :ref:`ToCharArray <toCharArray-examples>`
     - ``stringName.ToCharArray()``
     - Copies characters of string into character array.
   * - :ref:`ToString <string-toString-examples>`
     - ``stringName.ToString()``
     - Returns a string that represents the current object.


.. tip:: String methods can be combined in a process called **method chaining**. Given ``word = "C Sharp";``, ``word.ToUpper()`` returns ``C SHARP``. What would ``word.Substring(1,4).ToUpper()`` return?  `Try it at repl.it <https://repl.it/@launchcode/Intro-Into-Method-Chaining-CSharp#main.cs>`_.

Check Your Understanding
------------------------

Follow the links in the table above for the ``Replace``, ``Substring``, and ``Trim`` methods. Review the content and then answer the following questions.

.. admonition:: Question

   What is printed by the following code?

   .. sourcecode:: csharp
      :linenos:

      string language = "C Sharp";
      language.Replace('C', 'Q');
      language.Substring(0,5);
      Console.WriteLine(language);

   #. ``"C Sharp"``
   #. ``"Q Sharp"``
   #. ``"Q Sha"``
   #. ``"C Shar"``

.. admonition:: Question

   Given ``string language = 'C Sharp';``, what does ``language.Substring(1,4)`` return?

   #. ``" Sha"``
   #. ``"h"``
   #. ``"Shar"``
   #. ``"C Sh"``

.. admonition:: Question

   What is the value of the string printed by the following program?

   .. sourcecode:: csharp
      :linenos:

      string org = "  The LaunchCode Foundation ";
      string trimmed = org.Trim();

      Console.WriteLine(trimmed);

   #. ``"  The LaunchCode Foundation "``
   #. ``"The LaunchCode Foundation"``
   #. ``"TheLaunchCodeFoundation"``
   #. ``" The LaunchCode Foundation"``

..ans: "The LaunchCode Foundation"
