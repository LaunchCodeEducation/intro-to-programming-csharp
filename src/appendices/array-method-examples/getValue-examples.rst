.. _getValue-examples:

``GetValue`` Examples
=====================

The general syntax for this method is:

.. sourcecode:: csharp

   arrayName.GetValue(index)

This method returns the value of the specified index.

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
      
      Console.WriteLine(pets.GetValue(2));
      Console.WriteLine(pets.GetValue(8));
      

   **Output**

   ::

      Francis
      Unhandled Expectation: System.IndexOutOfRangeException
      
