.. _round-examples:

``Round()`` Examples
====================================

Two options: 
   1. Returns decimal number rounded to the nearest whole number.
   2. Rounds to specified decimal length.

**General Syntax**

.. sourcecode:: csharp

   //option 1
   Math.Round(number);

   //option 2
   Math.Round(number, decimalPlaces);




.. admonition:: Example

   .. sourcecode:: csharp
      :linenos:

      //rounding to nearest whole number
      Console.WriteLine(Math.Round(23.4));
      Console.WriteLine(Math.Round(-982.733426));


      //rounding to specified decimal length
      Console.WriteLine(Math.Round(-6328.34432, 2));
      Console.WriteLine(Math.Round(0.00992899823, 3));
      Console.WriteLine(Math.Round(Math.PI, 4));

   **Console Output**

   ::

      23
      -983

      -6328.34
      0.01
      3.1416


If you are curious about how rounding is determined, check out this `documentation <https://docs.microsoft.com/en-us/dotnet/api/system.math.round?view=net-5.0>`_.