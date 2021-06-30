.. _string-toString-examples:

``ToString`` Examples
==========================

Returns a string that represents the current object.  

General syntax for this method: 
   
.. sourcecode:: csharp

   
   stringName.ToString();



.. admonition:: Example
   
   .. sourcecode:: csharp

      double coffeePrice = 5.49;
      string coffeeString = coffeePrice.ToString();

      Console.WriteLine(coffeePrice.GetType());
      Console.WriteLine(coffeeString.GetType())

   **Output**

   .. sourcecode:: bash

      System.Double
      System.String




 