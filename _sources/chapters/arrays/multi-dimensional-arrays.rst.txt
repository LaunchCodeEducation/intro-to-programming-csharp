Multidimensional Arrays
==========================

Earlier we learned that arrays can store any type of value. If that is true, can we store arrays inside
of arrays? Well yes we can....

.. index:: ! multidimensional array

A **multidimensional array** is an collection of one dimensional arrays of the same length.  
Multidimensional arrays are often called "rectangular arrays", because the consistency in length of all the inner arrays.
The *inner* arrays must store the same data types as the outer array.


The figure below demonstrates a synonyms array that has arrays as values. The *inner* arrays contain words that
are synonyms of each other. Notice each inner array has an index position.

.. figure:: figures/multidim-array.png
   :alt: A label, synonyms, pointing to an array that contains arrays at it's four indexes. Each inner array has a list of words that are synonyms.

Two Dimensional Arrays
----------------------

The simplest form of a multidimensional array is a two dimensional array. A two dimensional array is like a
spreadsheet with rows and columns. To access items in a two dimensional array, use square bracket notation and
two indexes.  

Initializing Two Dimensional Arrays
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To declare a two-dimensional array, follow the data type with ``[,]``. 
This notation implies 2 dimensions, equal in length.  
When initializing, the brackets must be part of your new array.  You may fill in the rows and colums, or leave them empty.  
The code block below has the rows and columns filled in the initializing statement.


  
.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      int[,] numPractice = new int[3,4] 
      {
         {1, 2, 3, 4},
         {5, 6, 7, 8},
         {9, 10, 11, 12}
      };

Read the initializing bracket notation as "3 rows containing 4 values each".  
Multidimensional arrays will always be uniform in length no matter how many dimensions you go.  
For example, a three dimensional array uses the following notation: ``[2,2,7]`` 
could be read as "two arrays, two rows deep, containing 7 values each".

.. admonition:: Warning
   
   This is not the only way to initialize an multidimensional array, but this is the way the textbook will use.  Microsoft Documentation has other ways for delcaration and initializing, so if this method is not working for you `check them out <https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/multidimensional-arrays>`_ and use your favorite.


``Rank`` and ``Length`` Properties
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can still use the ``Length`` property with multidimensional arrays. With a multidimensional array, the length is based on all of the values the array contains.  
In this example, 3 rows of 4 values each, so 3 * 4 is 12.  

``Rank`` is useful when you want to verify the number of dimensions an array contains.  It will return an integer that represents the dimension.  
In the example below, a ``2`` is returned, which informs you that this array is two dimensional.


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      int[,] numPractice = new int[3,4] 
      {
         {1, 2, 3, 4},
         {5, 6, 7, 8},
         {9, 10, 11, 12}
      };
               
         Console.WriteLine(numPractice.Length);
         Console.WriteLine(numPractice.Rank);

   **Console Output**

   ::

      12
      2


Deterimining Dimensions
^^^^^^^^^^^^^^^^^^^^^^^^
When thinking about dimensions, look at the ``{ }`` in the array. Their placement within the array, and other arrays determines the dimensions.
Think of them like a staircase, the more steps into an array you take, the more dimensions you are in.

Using the ``numPractice`` code block above.  On **Line2** you will see the first ``{ }``, that would be the first dimension.  
**Line 3** has a second array contained in ``{ }``, the second dimension.  
**Line 4 and 5** have arrays, but they are contained within the first set of brackets, so still two dimensional.  
This pattern continues for however many dimensions you are working with.  


Accessing Values In Multiple Dimensions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
If you want to print or work with a specific value, you will need to reference both the row and column inside the ``[,]``.  

.. admonition:: Example

   Use the two dimensional array to print the following shuttleCrews members:  "Mae Jemison", "Ellen Ochoa", and "Winston Scott".

   .. sourcecode:: csharp
      :linenos:

      string[,] shuttleCrews = new string[3,3] 
      {
         {"Robert Gibson", "Mark Lee", "Mae Jemison"},
         {"Kent Rominger", "Ellen Ochoa", "Bernard Harris"},
         {"Eilen Collins", "Winston Scott",  "Catherin Coleman"}
      };

      Console.WriteLine(shuttleCrews[0,2]);
      Console.WriteLine(shuttleCrews[1,1]);
      Console.WriteLine(shuttleCrews[2,1]);

   **Console Output**

   ::

      Mae Jemison
      Ellen Ochoa
      Winston Scott


Beyond Two Dimensional Arrays
-----------------------------

Generally, there is no limit to how many dimensions you can have when creating
arrays. However it is rare that you will use more than two dimensions. Later on
in the class we will learn about more collection types that can handle complex
problems beyond the scope of two dimensional arrays.


Multidimensions and Array Methods
----------------------------------

Most array methods will only work on one dimensional arrays.  
Fortunately, the inner arrays within multidimensional arrays are one dimensional.  
It all comes down to accessing those inner arrays in order to manipulate them.  
We will learn how to access these more in the next chapter as we discuss loops.

For now, we can use many of them and verify the method worked with the help of bracket notation.

.. admonition:: Example

   Use bracket notation to update "Ori" with "Karl".

   .. sourcecode:: csharp
      :linenos:

      string[,] classRoster = new string[2,5] 
      {
         {"Rubi", "Ori", "Evelyn", "Alyce", "Willow" },
         {"Oliver", "Quintin", "Sato", "Olivia", "James"}
      };

      classRoster[0,1] = "Karl";

      Console.WriteLine(classRoster[0,1]);
   
   **Console OutPut**

   :: 

      Karl




Check Your Understanding
------------------------

.. admonition:: Question

   What is the two dimensional index for ``"Jones"``?

   .. sourcecode:: csharp
      :linenos:

      string[,] school = new string [2,3]
      { 
         {"science", "computer", "art"},
         {"Jones", "Willoughby", "Rhodes"}
      };

.. ans: school[1,0]
