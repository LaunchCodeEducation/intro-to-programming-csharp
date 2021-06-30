Working With Arrays
===================

Bracket Notation and Index
--------------------------

.. index:: ! index

As previously discussed, arrays are an ordered collection where each item can be accessed via index. 
Similar to strings, an **index** in an array is the number order given to items. 
Individual items can be accessed using bracket notation (``array[index]``).
Indexes are zero-based, going from ``0`` to ``array.Length-1``.

.. admonition:: Example

   Use bracket notation and index to access items in an array.

   .. sourcecode:: csharp
      :linenos:

      string[] programmingLanguages = new string[] {
         "JavaScript", // index 0
         "Python",     // index 1
         "Java",       // index 2
         "C#"          // index 3
      };
      Console.WriteLine(programmingLanguages[0]);
      Console.WriteLine(programmingLanguages[3]);

      // What will happen when index 4 is requested?
      Console.WriteLine(programmingLanguages[4]);

   **Console Output**

   ::

      JavaScript
      C#
      Unhandled Exception: System.IndexOutOfRangeException: Index was outside the bounds of the array.

Notice above that ``Unhandled Expectation: System.IndexOutOfRangeException: Index was outside the bounds of the array.`` was printed out when index 4 was referenced. This is returned when you request an index
that the array does not contain and you don't have a way to catch it.


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      string[] programmingLanguages = {"JavaScript", "Python", "Java", "C#"};
      Console.WriteLine(programmingLanguages[-1]);
      Console.WriteLine(programmingLanguages[100]);

   **Console Output**

   ::

      Unhandled Exception: System.IndexOutOfRangeException: Index was outside the bounds of the array.
       

Arrays are Mutable
------------------

.. index:: mutable

In programming, mutability refers to what happens when you attempt to change a value. Remember that strings are immutable, meaning that any change
to a string results in a new string being created. In contrast, arrays are **mutable**, meaning that individual items in
an array can be edited without a new array being created.

.. admonition:: Example

   Update an item in an array using bracket notation and index.

   .. sourcecode:: csharp
      :linenos:

      string[] cSharpDataTypes = ["int", "double", "string"];
      Console.WriteLine(cSharpDataTypes[0]);
      Console.WriteLine(cSharpDataTypes[1]);
      Console.WriteLine(cSharpDataTypes[2]);

      // Set the value of index 1 to be "decimal"
      cSharpDataTypes[1] = "decimal";

      // Notice the value at index 1 is now "decimal"
      Console.WriteLine(cSharpDataTypes[0]);
      Console.WriteLine(cSharpDataTypes[1]);
      Console.WriteLine(cSharpDataTypes[2]);

   **Console Output**

   .. sourcecode:: bash
     
     //original array
     int
     double
     string

     //updated array
     int
     decimal
     string

     

