.. _ceiling-examples:

``Ceiling()`` Examples
====================================

Rounds the number UP to closest whole number value.  Maintains original type.

Takes ``double`` and ``decimal`` types only.


**General Syntax**

.. sourcecode:: csharp

   Math.Ceiling(number);


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      double pos = 452.325;
      Console.WriteLine(Math.Ceiling(pos));
      Console.WriteLine(Math.Ceiling(932.0000000000004));
      Console.WriteLine(Math.Ceiling(100.00));
      
      //what if the numbers are negative?
      double neg = -452.325;
      Console.WriteLine(Math.Ceiling(neg));
      Console.WriteLine(Math.Ceiling(-938.0000000000004));
      Console.WriteLine(Math.Ceiling(100.00));

   **Console Output**

   ::

      453
      939
      100

      -452
      -938
      -100


   