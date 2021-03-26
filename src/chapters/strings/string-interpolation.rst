String Interpolation
=====================

Earlier, we used *concatenation* to combine strings and variables together in
order to create specific output:

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      string name = "Evelyn";
      int currentAge = 9;

      Console.WriteLine("Next year, " + name + " will be " + (currentAge + 1) + ".");

   **Console Output**

   ::

      Next year, Evelyn will be 10.

Unfortunately, this process quickly gets tedious for any output that depends on
multiple variables. Often, concatenation requires multiple test runs of the
code in order to check for syntax errors and proper spacing within the output.
Fortunately, C# offers us a better way to accomplish this process.

.. index:: ! string interpolation

**String Interpolation** allow for the automatic insertion of expressions
(including variables) into strings.  You can do this as you create the string without having to worry too much about proper syntax once you 
get the pattern.   

Interpolated strings are enclosed double quotes (``"``), like a regular sting, but you start the string with the ``$`` symbol.  As 
you create your string, you frame every variable reference in curly brackets ``{ }``, close with a final ``"`` and end with a ``;``.  


.. admonition:: Example

   String Interpolation allows for variables and other expressions to be directly
   included in strings.

   .. sourcecode:: bash
      :linenos:

      string name = "Evelyn";
      int currentAge = 9;

      Console.WriteLine($"Next year, {name} will be {currentAge + 1}.");

   **Console Output**

   ::

      Next year, Evelyn will be 10.



.. admonition:: Note

   The 6th edition of C# added string interpolation in 2015. Not only is string
   interpolation relatively new to C#, but you may encounter Composit Formatting. 
   This is very similar, but cumbersome with syntax.  This method is used within some of the
   documentation you may find, so we will walk through it.

Composit Format Strings
-----------------------

Composit formatting is typically used for larger data types in C#, such as objects.  Strings are objects, so that is why we can use this 
type of formatting on them as well.  

Creating a composite string is very simiple, and similar to interpolation.  It uses ``{ }`` as well, but no ``$``.

.. sourcecode:: csharp
   :linenos:

   string name = "Evelyn";
   int currentAge = 9;
   int ageNextYear = currentAge + 1;

   Console.WriteLine("Next year, {0} will be {1}.", name, ageNextYear);

**Console Output**

::

   Next year, Evelyn will be 10.

Instead of directly referencing the variables within the string, we create placeholders which we number.  
We close the string with ``"``, place a ``,`` and then list the variables in the order we want to use them.



Check Your Understanding
------------------------

.. admonition:: Question

   Mad Libs are games where one player asks the group to supply random words
   (e.g. "Give me a verb," or, "I need a color"). The words are substituted
   into blanks within a story, which is then read for everyone's amusement. In
   elementary school classrooms, giggles and hilarity often ensue. TRY IT!

   Refactor the following code to replace the awkward string concatenation with string interpolation. 
   Be sure to add your own choices for the variables.

   .. replit:: csharp
      :linenos:
      :slug: String-Mad-Lib-CSharp

      string pluralNoun = ;
      string name = ;
      string verb = ;
      string adjective = ;
      string color = ;

      Console.WriteLine("C# provides a "+ color +" collection of tools — including " + adjective + " syntax and " + pluralNoun + " — that allows "+ name +" to "+ verb +" with strings.");

