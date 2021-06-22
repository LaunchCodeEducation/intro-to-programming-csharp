.. _array-sort-examples:

``Sort`` Examples
=====================

The general syntax for this method is:

.. sourcecode:: csharp

   Array.Sort(arrayName)

This method puts the elements of the array in ascending or alphabetical order.

.. admonition:: Example

   Sort the entire array.

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
      
      Console.WriteLine(pets.GetValue(1));
      
      Array.Sort(pets);
      
      Console.WriteLine(pets.GetValue(1));
      

   **Output**

   ::

      Thisbe
      Beatrice


Sorting Sections
------------------


Sorting a section of an array is possible, too.  The general syntax is as follows:

.. sourcecode:: csharp

   Array.Sort(arrayName, startingIndex, rangeIndex);

.. admonition:: Try It!

   .. replit:: csharp
      :linenos:
      :slug: SortArrayMethod-CSharp
      
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
      
      
      Array.Sort(pets, 0, 3);
      