.. _truncate-examples:

``Truncate`` Examples
====================================

Returns a ``double`` value or ``decimal`` value to the whole number WITHOUT rounding.

.. sourcecode:: csharp

   Math.Truncate(number);


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      double test = -129.768009;
      Console.WriteLine(Math.Truncate(test));
      Console.WriteLine(Math.Truncate(59.22));

      Console.WriteLine(test.GetType());

   **Console Output**

   ::

      -129
      59

      System.Double


Note that the value printed is the numbers that preceeded the decimal point.  
Truncate does NOT round, only shortens.  
While the output looks like an ``int`` type, it is still a ``double``.