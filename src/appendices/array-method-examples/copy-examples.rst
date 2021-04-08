.. _copy-examples:

``Copy`` Examples
=====================

The general syntax for this method is:

.. sourcecode:: csharp

   Array.Copy(originalArray, copiedArray, numItems)

This method returns a new array with the designated values copied from the original array to an new array.

.. admonition:: Example

   Create a copy of the array ``areaCodes``.

   .. sourcecode:: csharp
      :linenos:

      int[] areaCodes = new int[] {314, 703, 202, 207, 636};
      int[] otherAreaCodes = new int[5];

      Array.Copy(areaCodes, otherAreaCodes, 5);

      Console.WriteLine(otherAreaCodes[0]);
      Console.WriteLine(otherAreaCodes[1]);
      Console.WriteLine(otherAreaCodes[2]);
      Console.WriteLine(otherAreaCodes[3]);
      Console.WriteLine(otherAreaCodes[4]);

   **Output**

   ::

      314
      703
      202
      207
      636
      
