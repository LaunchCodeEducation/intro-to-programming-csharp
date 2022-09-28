.. _join-examples:

``Join`` Examples
====================

This method returns a new string of items from an array joined by a designated separator between each item.
The general syntax for this method is:

.. sourcecode:: csharp

   string variableName = string.Join(separator, arrayName);

.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:
      
      string[] fruits = new string[] { "watermelon", "kiwi", "gooseberry"};

      string fruitSalad = string.Join("::", fruits);

      Console.WriteLine(fruitSalad);
      

   **Output**

   ::

      watermelon::kiwi::gooseberry
      

The separator is up to you.  Just remember the final outcome is turning your array into a string.