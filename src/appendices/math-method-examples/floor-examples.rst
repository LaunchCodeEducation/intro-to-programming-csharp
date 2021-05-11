.. _floor-examples:

``Floor()`` Examples
====================================

Rounds the number DOWN to closest whole number value.  Maintains original type.

Requires ``double`` or ``decimal`` types.


**General Syntax**

.. sourcecode:: csharp

   Math.Ceiling(number);


.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      double pos = 452.325;
      Console.WriteLine(Math.Floor(pos));
      Console.WriteLine(Math.Floor(938.0000000000004));
      Console.WriteLine(Math.Floor(100.00));
      
      //what if the numbers are negative?
      double neg = -452.325;
      Console.WriteLine(Math.Floor(neg));
      Console.WriteLine(Math.Floor(-938.0000000000004));
      Console.WriteLine(Math.Floor(100.00));

   **Console Output**

   ::

      452
      938
      100

      -453
      -939
      -100


   