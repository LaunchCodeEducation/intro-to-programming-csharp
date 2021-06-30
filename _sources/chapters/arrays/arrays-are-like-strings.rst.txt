Arrays Are Like Strings
=======================

.. index:: ! array

Arrays are similar to strings, but are a more general collection type. 
Like strings, **arrays** are a sequence of values of one data type that 
can be accessed via an ordered index.

The figure below demonstrates an array of named languages. The array contains
four strings, each of those values has an index position.

.. figure:: figures/Arrays-are-like-strings.png
   :alt: A label, languages, pointing to an array that contains "Python" at index 0, "C#" at index 1, "Java" at index 2, and "JavaScript" at index 3.

Declaring an Array
------------------

.. index::
   single: array; literal

Programmers use multiple ways to declare and initialize a new array.  
In C#, arrays are of a static length.  This means that that you need to
declare the length upon initialization.  With that in mind, we will walk through
a few ways to delcare and initialize arrays.  


The ``new`` Operator
^^^^^^^^^^^^^^^^^^^^^^

``new`` is an operator keyword that creates a new instance of a specific data type.   
When you create an array, you delcare it on the left-hand side of the ``=``.  You 
initialize it on the right side of the ``=`` and must use ``new`` to let the compiler know that the values placed
into your array, or other collection class, are new and unique.  

.. sourcecode:: csharp
   :linenos:

   double[] studentGrades = new double[12];
   
   string[] programmingLanguages = new string[] {"JavaScript", "Python", "Java", "C#"};

   
 

The array on **Line 1** was delcared, but we haven't filled it yet.  
Instead we delcared that it will hold 12 double data type values by using bracket notation:  ``new double[12]``.  
This allows us to fill the array later in our program.

The array on **Line 3** was initialized and filled immediately with a list of popular 
programming languages within ``{ }``.   Since we filled it right away, we don't have to 
declare a size.  The compiler is able to count how many values are contained within the array.

Array items can also be declared on multiple lines, separated by commas.

.. sourcecode:: csharp
   :linenos:

   string[] cSharpDataTypes = new string[] {
      "int",
      "double",
      "string",
   };

Arrays can also start out empty, waiting to be filled within your program. 

.. sourcecode:: csharp
   :linenos:

   string[] studentNames;

   studentNames = new string[] {"Oliver", "Evelyn", "Alyce"}


Declaring without ``new``
^^^^^^^^^^^^^^^^^^^^^^^^^^

When you initialize upon declaration, it is possible to avoid the keyword ``new``.  

.. sourcecode:: csharp
   :linenos:

   int[] numDesks = { 12, 22, 17, 23 }; 


Array Length
------------

To check the length of an array, use the ``Length`` property, just like with
strings. C# array length is static, but we don't have to declare the length directly with 
each initialization.  

.. note::

   In other languages, such as JavaScript, arrays are dynamic in length and do not require length of the array to be declared upon creation.


.. admonition:: Example

   Print out the length of the array.

   .. sourcecode:: csharp
      :linenos:

      string[] programmingLanguages = {"JavaScript", "Python", "Java", "C#"};
      Console.WriteLine(programmingLanguages.Length);

   **Console Output**

   ::
      
      4



Check Your Understanding
------------------------

.. admonition:: Question

   What is the length of each array?

   .. sourcecode:: csharp
      :linenos:
      
      string[] classes = {"science, computer, art, literature"};

      string[] teachers = {"Jones", "Willoughby", "Rhodes", "Montross"};


   
