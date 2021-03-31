.. _lastIndexOf-examples:

``LastIndexOf`` Examples
===========================

The general syntax for this method is:

.. sourcecode:: csharp

   Array.IndexOf(arrayName, item)

This method returns the index of the LAST occurence of an item in the array.
If the item is not in the array, -1 is returned.

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
      
      Console.WriteLine(Array.LastIndexOf(pets, "Beatrice"));
      Console.WriteLine(Array.LastIndexOf(pets, "Poppy"));
      

   **Output**

   ::

      6
      -1
