.. _split-examples:

``Split`` Examples
====================

``Split`` is actually a string method, but it complements the array method ``Join``.

``Split`` divides a string into smaller pieces, which are stored in a new array. 
The ``delimiter`` argument determines how the string is broken apart.

The general syntax for this method is:

.. sourcecode:: csharp

   string[] arrayName = stringName.Split(delimiter);
   

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
	   string fruitSalad = "watermelon--kiwi--gooseberry";
         
      string[] fruits = fruitSalad.Split("--");
      
      Console.WriteLine(fruits[0]);
      Console.WriteLine(fruits[1]);
      Console.WriteLine(fruits[2]);
      
   **Output**

   ::

      watermelon
      kiwi
      gooseberry
      

The delimiter MUST match what is used by the string. 