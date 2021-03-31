.. _resize-examples:

``Resize`` Examples
=====================

The general syntax for this method is:

.. sourcecode:: csharp

   Array.Resize(ref arrayName, size);

This method will add or remove indices based on the new size.

To elongate the array, use the syntax:  

.. sourcecode:: csharp

   Array.Resize(ref arrayName, arrayName.Length + integer);


To shorten the array, use the following syntax:

.. sourcecode:: csharp

   Array.Resize(ref arrayName, integer);

The integer must be smaller than the length of the original, or an error will be thrown.


New keyword ``ref`` is used here.  This method returns a **new** array meeting your new size requirements.  
The keyword ``ref`` is saying that all the changes we are making will be reflected in the updated array. 


Extending Your Array
----------------------

.. admonition:: Example

   Extend the array by 2 placeholders.

   .. sourcecode:: csharp
      :linenos:

      string[] pets = new string[]  
      { 
         "Alyce", 
         "Thisbe", 
         "Francis", 
         "Scratch", 
         "Beatrice", 
         "Shadow", 
         "Beatrice"
      };
      
      Console.WriteLine(pets.Length);
      
      Array.Resize(ref pets, pets.Length + 2);
      
      Console.WriteLine(pets.Length);
      

   **Output**

   ::

      7
      9

This can be a great method for adding additonal values to the end of your array. 


Reducing Your Array
--------------------

.. admonition:: Example

   Reduce the size of the array to 3 values.

   .. sourcecode:: csharp
      :linenos:
      
      int[] myNums = new int[] { 10, 3, 4, 8, 12, 12};

      Console.WriteLine(myNums.Length);

      Array.Resize(ref myNums, 3);
            
      Console.WriteLine(myNums.Length);

   **Console Output**

   ::
      
      6
      3