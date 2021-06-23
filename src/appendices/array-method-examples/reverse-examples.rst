.. _array-reverse-examples:

``Reverse`` Examples
=====================

The general syntax for this method is:

.. sourcecode:: csharp

   Array.Reverse(arrayName)

This method reverses the order of the indices.

.. admonition:: Example

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
      
      Array.Reverse(pets);
      
      Console.WriteLine(pets.GetValue(1));
      

   **Output**

   ::

      Thisbe
      Shadow


Reversing Sections
-------------------

Reversing a section of an array is possible, too.  The general syntax is as follows:

.. sourcecode:: csharp

   Array.Reverse(arrayName, startingIndex, rangeIndex);

.. admonition:: Example

   .. replit:: csharp
      :linenos:
      :slug: Reverse-Array-Method-CSharp
      
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
      
      
      Array.Reverse(pets, 0, 3);
      
      
   
      

If you are looking for reverse alphabetical order, 
you will need to use this along with the ``Sort`` :ref:`method <array-sort-examples>`.