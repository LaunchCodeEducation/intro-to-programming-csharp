.. _foreach-examples:

``foreach`` Examples
=====================

This is an easier alternative to the ``for`` loop.  
The ``foreach`` loop iterated through each item in a collection or array.  
You can enclose statements inside of this loop, as you would a ``for`` loop.

Unlike a ``for`` loop, this loop does not keep track of the index, and will only iterate in a forward direction.

.. sourcecode:: csharp
   :linenos:

   foreach(data-type variable-name in collection-variable)
   {
      //statements to be executed
   }


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      List<int> numbers = new List<int>();

      numbers.Add(14);
      numbers.Add(18);
      numbers.Add(19);
      numbers.Add(21);

      foreach(int num in numbers)
      {
         if(num % 2 == 0)
         {
            Console.WriteLine(num);
         }
      }

   **Output**

   ::

      14
      18